---
title: Erişim yerinde Azure AD alanına aygıttan Microsoft 365 iş kaynakları
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
ms.assetid: b0f4d010-9fd1-44d0-9d20-fabad2cdbab5
description: İş kolu uygulamaları, dosya paylaşımları ve yazıcılar Azure Active Directory'den Windows 10 aygıt katıldı gibi yerinde kaynaklara erişmek nasıl öğrenin.
ms.openlocfilehash: 0a5d4b0828888fcb99676223000c446479f84ddc
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26982260"
---
# <a name="access-on-premises-resources-from-an-azure-ad-joined-device-in-microsoft-365-business"></a>Erişim yerinde Azure AD alanına aygıttan Microsoft 365 iş kaynakları

Azure Active Directory alanına dahil olan herhangi bir Windows 10 aygıt Office 365 uygulamalarınızı gibi tüm bulut tabanlı kaynaklara erişebilir ve Microsoft 365 işletme tarafından korunabilir. Ayrıca şirket içi iş satır (LOB) uygulamaları, dosya paylaşımları ve yazıcılar gibi kaynaklar için erişim sağlamak için [Azure AD Connect](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnect)kullanarak, şirket içi Active Directory Azure Active Directory ile eşitlenmelidir. Daha fazla bilgi için [Aygıt Yönetimi Azure Active Directory'de giriş](https://docs.microsoft.com/en-us/azure/active-directory/device-management-introduction) konusuna bakın. 
  
## <a name="run-azure-ad-connect"></a>Bağlanma Azure AD Çalıştır

Şirket içi kaynaklara erişmek, kuruluşunuzun Azure AD alanına bağlı aygıtları etkinleştirmek için aşağıdaki adımları izleyin.
  
1. Azure Active Directory'ye, kullanıcıları, grupları ve yerel Active Directory'den kişileri eşitlemek için dizin eşitleme Sihirbazı'nı çalıştırın ve [Office 365 için'dizin eşitlemeyi ayarlamak](https://support.office.com/article/1b3b5318-6977-42ed-b5c7-96fa74b08846)Azure AD Bağlan olarak açıklanmıştır.
    
2. Dizin eşitleme tamamlandıktan sonra kuruluşunuzun Windows 10 aygıtları Azure AD alanına dahil olduğundan emin olun. Bu adım, tek tek her Windows 10 aygıtta yapılır. [Microsoft 365 iş kullanıcıları için Windows aygıtları ayarlayın](set-up-windows-devices.md) ayrıntılı bilgi için bkz. 
    
3. Windows 10 aygıtları Azure AD alanına dahil olduğunda, her kullanıcının kendi aygıtları ve Microsoft 365 iş kimlik bilgileri ile oturum açma yeniden. Tüm aygıtlar artık yerinde kaynaklara erişebilir.
    
Erişim aygıtları Azure Reklam kaynakları birleştirilmiş yerinde almak için hiçbir ek işlem gereklidir. Windows 10 kullanılabilir yerleşik işlevsellik budur. 
  
Kuruluşunuzun Azure AD alanına bağlı aygıt yukarıda açıklanan yapılandırma dağıtmak hazır değilse, [karma Azure AD katılmış aygıt yapılandırması](manage-windows-devices.md)ayarlama göz önünde bulundurun.
  
### <a name="considerations-when-joining-your-windows-devices-to-azure-ad"></a>Aygıtlarınızın Windows Azure AD katılırken dikkat edilmesi gereken noktalar

Azure AD katılmadan önce etki alanına katılmış Windows aygıtı varsa veya bir çalışma grubunda, aşağıdaki kısıtlamaları göz önüne almanız gerekir:
  
- Bir aygıtı Azure AD katıldığında, varolan bir profili başvurulmadan yeni bir kullanıcı oluşturur. Bu sorunu gidermek için profillerini el ile geçirilmesi gerekir. Kullanıcı profili, Sık Kullanılanlar, yerel dosyalar, tarayıcı ayarlarını, Başlat menüsü ayarlarını, vb. gibi bilgileri içerir. Varolan dosyalarınızı ve ayarlarınızı yeni profile eşlemek için bir üçüncü taraf aracı bulmak için en iyi yaklaşım olduğunu
    
- Grup İlkesi nesneleri (GPO) aygıtı kullanıyor olsa da, bazı GPO'ları bir karşılaştırılabilir [Yapılandırma hizmeti sağlayıcısı](https://docs.microsoft.com/windows/configuration/provisioning-packages/how-it-pros-can-use-configuration-service-providers) (CSP) içinde Intune olmayabilir. Varolan GPO'lar için karşılaştırılabilir CSP bulmak için [MMAT aracını](https://www.microsoft.com/download/details.aspx?id=45520) çalıştırın. 
    
- Active Directory kimlik doğrulamasını kullanan uygulamalar için kimlik doğrulama olanağınız olur. Çalışılabilecek bu eski bir uygulama kullanarak değerlendirmek ve mümkünse modern kimlik doğrulama kullanan bir uygulama için güncelleştirme göz önünde bulundurun.
    
- Active Directory yazıcı bulma çalışmaz. Bu sorunu gidermek için tüm kullanıcılar için doğrudan yazıcı yolları sağlamak veya [Karma bulut baskı](https://docs.microsoft.com/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-deploy)yelpazesinin.
    
