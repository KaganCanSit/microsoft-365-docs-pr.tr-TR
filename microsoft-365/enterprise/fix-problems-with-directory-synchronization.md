---
title: Microsoft 365 için dizin eşitleme sorunlarını düzeltme
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
ms.localizationpriority: high
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- admindeeplinkMAC
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Office 365 dizin eşitlemesiyle ilgili sorunların yaygın nedenlerini açıklar ve bunları gidermeye ve çözmeye yardımcı olacak birkaç yöntem sağlar.
ms.openlocfilehash: 248ccc888f047a57f474dfc55b501f4450cb116e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101017"
---
# <a name="fixing-problems-with-directory-synchronization-for-microsoft-365"></a>Microsoft 365 için dizin eşitleme sorunlarını düzeltme

Dizin eşitlemesi ile şirket içi kullanıcıları ve grupları yönetmeye devam edebilir, eklemeleri, silmeleri ve değişiklikleri bulutta eşitleyebilirsiniz. Ancak kurulum biraz karmaşıktır ve bazen sorunların kaynağını belirlemek zor olabilir. Olası sorunları belirlemenize ve çözmenize yardımcı olacak kaynaklarımız vardır.
  
## <a name="how-do-i-know-if-something-is-wrong"></a>Bir sorun olup olmadığını Nasıl yaparım? biliyor musun?

Microsoft 365 yönetim merkezi'daki DirSync Durumu kutucuğu bir sorun olduğunu gösterdiğinde bir sorun olduğunun ilk göstergesidir.
  
Ayrıca, Microsoft 365 kiracınızın dizin eşitleme hatalarıyla karşılaştığını belirten bir posta (alternatif e-postaya ve yönetici e-postanıza) alırsınız. Ayrıntılar için bkz. [Microsoft 365 dizin eşitleme hatalarını tanımlama](identify-directory-synchronization-errors.md).
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>Azure Active Directory Bağlan aracı edinmek Nasıl yaparım??

[Microsoft 365 yönetim merkezi](https://admin.microsoft.com) **Etkin Kullanıcılar'a** \> gidin.<a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank"></a> **Diğer** menüsüne (üç nokta) tıklayın ve **Dizin eşitlemesi'ni** seçin. 
  
Azure AD Bağlan indirmek için [sihirbazdaki yönergeleri](set-up-directory-synchronization.md) izleyin. 
  
Azure Active Directory (Azure AD) Eşitleme (DirSync) kullanmaya devam ediyorsanız, [Microsoft 365'da Azure Active Directory Eşitleme Aracı yükleme ve Yapılandırma Sihirbazı hata iletilerini giderme](/troubleshoot/azure/active-directory/installation-configuration-wizard-errors) bölümüne göz atın  dirsync'i yüklemek için sistem gereksinimleri, ihtiyacınız olan izinler ve yaygın hataları giderme hakkında bilgi için. 
  
Azure AD Eşitleme'den Azure AD Bağlan'ye güncelleştirmek için [yükseltme yönergelerine](/azure/active-directory/hybrid/how-to-dirsync-upgrade-get-started) bakın.
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-microsoft-365"></a>Microsoft 365'de dizin eşitlemesiyle ilgili sorunların yaygın nedenlerini çözme

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>Eşitlenmiş nesneler çevrimiçi olarak görünmüyor veya güncelleştirilmiyor veya Hizmetten eşitleme hata raporları alıyorum.

- [Kimlik eşitleme ve yinelenen özniteliklerin dayanıklılığı](/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>Yönetim merkezinde bir uyarım var veya son eşitleme olayı olmadığını belirten otomatik e-postalar alıyorum
- [Azure AD Connect'in bağlantı sorunlarını giderme](/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [Azure AD Connect Hesapları ve izinleri](/azure/active-directory/hybrid/reference-connect-accounts-permissions)
- [Azure AD Connect eşitlemesi: Azure AD hizmet hesabını yönetme](/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [Azure Active Directory’ye dizin eşitlemesi duruyor veya eşitlemenin bir günden daha uzun süredir kayıt yapmadığına dair uyarı alıyorsunuz](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>Parola karmaları eşitlenmiyor veya yönetim merkezinde son parola karması eşitlemesinin yapılmadığına dair bir uyarı görüyorum
- [Azure AD Connect eşitlemesiyle parola karması eşitlemesini uygulama](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>Nesne kotası aşıldığını belirten bir uyarı görüyorum
- Hizmetin korunmasına yardımcı olmak için yerleşik bir nesne kotamız var. Dizininizde Microsoft 365 eşitlemesi gereken çok fazla nesne varsa kotanızı artırmak [için İş ürünleri için desteğe başvurmanız](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) gerekir.

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>Hangi özniteliklerin eşitleneceğini bilmem gerekiyor
- Şirket içi ile bulut arasında eşitlenen tüm özniteliklerin listesini [burada](https://go.microsoft.com/fwlink/p/?LinkId=396719) bulabilirsiniz.

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>Bulutla eşitlenmiş nesneleri yönetemiyorum veya kaldıramıyorum
- Yalnızca buluttaki nesneleri yönetmeye hazır mısınız? Ya da şirket içinde silinmiş ancak bulutta takılı kalmış bir nesne var mı? Bu sorunların nasıl çözüleceğini gösteren yönergeler için bu Eşitleme ve [destek sırasında](/troubleshoot/azure/active-directory/cannot-manage-objects) karşılaşılan [sorun giderme](/azure/active-directory/hybrid/tshoot-connect-sync-errors) makalesine göz atın.

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>Şirketimin eşitlenebilen nesne sayısını aştığını belirten bir hata iletisi aldım
- Bu sorun hakkında daha fazla bilgiyi [burada](/troubleshoot/azure/active-directory/exceed-number-objects-synced) bulabilirsiniz.
   
## <a name="other-resources"></a>Diğer kaynaklar

- [Yinelenen kullanıcı asıl adlarını düzeltme betiği](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [Yönlendirilemeyen bir etki alanını (.local etki alanı gibi) dizin eşitlemesi için hazırlama](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [Eşitlenen nesnelerin toplam sayısını saymak için betik](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [AD FS 2.0 sorunlarını giderme](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [Posta özellikli gruplar için boş DisplayName özniteliklerini düzeltmek için PowerShell kullanma](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [Yinelenen UPN'yi düzeltmek için PowerShell kullanma](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [Yinelenen e-posta adreslerini düzeltmek için PowerShell kullanma](https://go.microsoft.com/fwlink/p/?LinkId=396731)
