---
title: Etki alanı için dizin eşitlemesi sorunlarını Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Office 365'ta dizin eşitlemesi sorunlarının yaygın nedenlerini açıklar ve sorunları gidermeye ve çözmeye yardımcı olmak için birkaç yöntem sağlar.
ms.openlocfilehash: dba6626ead648928186f8fbeac646a2b52206bc0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988626"
---
# <a name="fixing-problems-with-directory-synchronization-for-microsoft-365"></a>Etki alanı için dizin eşitlemesi sorunlarını Microsoft 365

Dizin eşitlemeyle, şirket içinde kullanıcıları ve grupları yönetmeye devam eder, ayrıca eklemeleri, silmeleri ve değişiklikleri buluta eşitlersiniz. Ancak kurulumu biraz karmaşıktır ve bazen sorunların kaynağını belirlemek zor olabilir. Olası sorunları tanımlamanıza ve düzeltmeye yardımcı olacak kaynaklarımız vardır.
  
## <a name="how-do-i-know-if-something-is-wrong"></a>Bir sorun olup olduğunu nasıl bilim?

Bir şeyin yanlış olduğuna dair ilk gösterge, kutucukta yer alan DirSync Durumu kutucuğunun Microsoft 365 yönetim merkezi bir sorun olduğunu göstergesidir.
  
Kiracınız tarafından dizin eşitleme hatalarına neden olduğunu belirten bir posta da (alternatif e-postaya veya yönetici e-postanıza) Microsoft 365 gönderilir. Ayrıntılar için bkz[. Çalışma sayfalarında dizin eşitleme Microsoft 365](identify-directory-synchronization-errors.md).
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>Yeni araç Azure Active Directory Bağlan edinebilirsiniz?

Gezinti [Microsoft 365 yönetim merkezi](https://admin.microsoft.com) Etkin **kullanıcılar'a** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**gidin**</a>. Diğer **menüsüne** (üç nokta) tıklayın ve Dizin **eşitlemesi'ne tıklayın**. 
  
Azure [AD'i indirmek için](set-up-directory-synchronization.md) sihirbazda verilen yönergeleri Bağlan. 
  
Azure Active Directory (Azure AD) Eşitleme'yi (DirSync) kullanmaya devam ediyorsanız Azure Active Directory, Azure Active Directory Eşitleme Aracı yüklemesi ve Yapılandırma Sihirbazı hata iletileriyle ilgili sorunları [giderme Microsoft 365](/troubleshoot/azure/active-directory/installation-configuration-wizard-errors)  dirsync'i yüklemek için sistem gereksinimleri, size gereken izinler ve yaygın hataların nasıl giderilir hakkında bilgi almak için. 
  
Azure AD Eşitleme'dan Azure AD Bağlan'e güncelleştirmek için, [yükseltme yönergelerine bakın](/azure/active-directory/hybrid/how-to-dirsync-upgrade-get-started).
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-microsoft-365"></a>E-Microsoft 365'de dizin eşitlemesi ile ilgili sorunların yaygın Microsoft 365

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>Eşitlenmiş nesneler görünmüyor veya çevrimiçi olarak güncelleştiriliyor ya da Hizmetten eşitleme hatası raporları alıyorum.

- [Kimlik eşitleme ve yinelenen özniteliklerin dayanıklılığı](/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>Yönetim merkezinde uyarım var veya yakın zamanda eşitleme etkinliği olmadığını haber alan otomatik e-postalar alıyorum
- [Azure AD Connect'in bağlantı sorunlarını giderme](/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [Azure AD Connect Hesapları ve izinleri](/azure/active-directory/hybrid/reference-connect-accounts-permissions)
- [Azure AD Connect eşitlemesi: Azure AD hizmet hesabını yönetme](/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [Azure Active Directory’ye dizin eşitlemesi duruyor veya eşitlemenin bir günden daha uzun süredir kayıt yapmadığına dair uyarı alıyorsunuz](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>Parola karmaları eşit görmüyor veya yönetim merkezinde yakın zamanda parola karması eşitlemesi olmadığının bir uyarısını görüyorum
- [Azure AD Connect eşitlemesiyle parola karması eşitlemesini uygulama](/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>Nesne kotasının aşıldı uyarısını görüyorum
- Hizmetin korunmasına yardımcı olmak için yerleşik bir nesne kotası var. Dizinde birden çok nesne varsa ve bu nesnelerin Microsoft 365, kotanızı artırmak için İş ürünleri için [de destek'e](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) başvurun.

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>Hangi özniteliklerin eşitlenmiş olduğunu bil ihtiyacım var
- Burada, şirket içiyle bulut arasında eşitlenen tüm özniteliklerin listesini [bulabilirsiniz](https://go.microsoft.com/fwlink/p/?LinkId=396719).

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>Bulutla eşitlenmiş olan nesneleri yönete bilmiyorum veya kaldıram
- Nesneleri yalnızca bulutta yönetmeye hazır mısınız? Yoksa şirket içinde silinmiş ama bulutta takılıp kalmış bir nesne mi var? Bu sorunların çözümünde yol gösterici [sorunlar için Eşitleme](/azure/active-directory/hybrid/tshoot-connect-sync-errors) sırasında Sorunları [Giderme ve](/troubleshoot/azure/active-directory/cannot-manage-objects) destek makalesine göz atabilirsiniz.

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>Şirketimin eşitlenmeyecek nesne sayısını aşmış olduğunu haber aldım
- Bu sorun hakkında burada daha fazla yazı [okuyabilirsiniz](/troubleshoot/azure/active-directory/exceed-number-objects-synced).
   
## <a name="other-resources"></a>Diğer kaynaklar

- [Yinelenen kullanıcı asıl adlarını düzeltme betiği](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [Yönlendirilebilir olmayan etki alanını (.local etki alanı gibi) dizin eşitlemesi için hazırlama](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [Eşitlenmiş toplam nesneleri saymak için betik](/samples/browse/?redirectedfrom=TechNet-Gallery)
    
- [AD FS 2.0 sorunlarını giderme](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [Posta özellikli grupların boş DisplayName özniteliklerini düzeltmek için PowerShell kullanma](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [Yinelenen UPN'leri düzeltmek için PowerShell kullanma](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [Yinelenen e-posta adreslerini düzeltmek için PowerShell kullanma](https://go.microsoft.com/fwlink/p/?LinkId=396731)
