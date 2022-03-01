---
title: Microsoft Yönetilen Masaüstü için önkoşullar
description: Microsoft Yönetilen Masaüstü'ne kaydolmadan önce Microsoft 365 için lisanslar, Azure hesapları, kimlik doğrulama ayarları ve güvenlik ayarları
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 495aa7e505bdcec8b5848499ac688847afa129bc
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011834"
---
# <a name="prerequisites-for-microsoft-managed-desktop"></a>Microsoft Yönetilen Masaüstü için önkoşullar

<!--This topic is the target for a "Learn more" link in the Admin Portal (aka.ms/prereq-azure). DO NOT DELETE.-->
<!--from Prerequisites -->

Bu makalede, Microsoft Yönetilen Masaüstü ile başarılı olmak için karşılamanız gereken altyapı gereksinimleri ana hatlarıyla açıklanmıştır.

| Alan | Önkoşul ayrıntıları |
| ----- | ----- |
| Lisanslama | Microsoft Yönetilen Masaüstü için Microsoft 365 E3 uç nokta (veya eşdeğerleri) için Microsoft Defender ile birlikte Lisans atamanız gerekir. <ul><li>Belirli hizmet planları hakkında ayrıntılı bilgi için bkz. [Lisanslar hakkında daha fazla bilgi](#more-about-licenses).</li><li> Kullanılabilir lisanslar hakkında daha fazla bilgi için lisans [Microsoft 365 bakın](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans).</li></ul>
| Bağlantı | Tüm Microsoft Yönetilen Masaüstü cihazları, şirket ağına gelen çok sayıda Microsoft hizmeti uç noktasına bağlantı gerektirir.<br><br> Gerekli IP'lerin ve URL'lerin tam listesi için bkz. [Ağ yapılandırması](../get-ready/network.md).
| Azure Active Directory | Azure Active Directory (Azure AD) tüm kullanıcı hesaplarının yetkili kaynağı olmalıdır veya kullanıcı hesapları, Azure AD'nin desteklenen en son sürümü kullanılarak şirket içi Active Directory'den eşitlen Bağlan. <ul><li>Daha fazla bilgi için [bkz. Azure AD Bağlan](/azure/active-directory/hybrid/whatis-azure-ad-connect).</li><li> Desteklenen Azure AD sürümler hakkında daha fazla Bağlan için bkz. [Azure AD Bağlan:Sürüm geçmişi](/azure/active-directory/hybrid/reference-connect-version-history).</li></ul>
| Kimlik Doğrulama | Kullanıcı hesapları için birincil kimlik doğrulamasının kaynağı Azure AD değilse, Azure AD kimlik doğrulama yöntemlerinde aşağıdaki kimlik doğrulama yöntemlerinden birini Bağlan:<ul><li> Parola karması eşitlemesi.</li> <li> Geçişli kimlik doğrulama.</li><li>Azure AD tümleştirme gereksinimlerini karşılamak için Windows Server ADFS ve Microsoft olmayan IDP'ler dahil) dış kimlik sağlayıcısı. Daha fazla bilgi için yönergelere [bakın](https://www.microsoft.com/download/details.aspx?id=56843).</li></ul> <br> Azure AD kimlik doğrulama seçenekleri Bağlan ayarlarken parola geri yazma da önerilir. Daha fazla bilgi için bkz [. Parola geri yazma](/azure/active-directory/authentication/howto-sspr-writeback). <br><br> Dış kimlik sağlayıcısı uygulanırsa, çözümü doğrulamalısiniz:<ul><li>Azure AD tümleştirme gereksinimlerini karşılar.</li><li>Microsoft Yönetilen Masaüstü cihaz uyumluluk ilkesine izin veren Azure AD Koşullu Erişimi destekler.</li><li>Microsoft Yönetilen Masaüstü kapsamında gerekli cihaz Microsoft 365, bilgisayar hizmetleri veya özelliklerinin kullanımını sağlar.</li></ul> <br>Azure AD ile kimlik doğrulama seçenekleri hakkında daha fazla bilgi için bkz. [Azure AD Bağlan açma seçenekleri.](/azure/active-directory/connect/active-directory-aadconnect-user-signin)
| Microsoft 365 | OneDrive İş Microsoft Yönetilen Masaüstü kullanıcıları için etkinleştirilmesi gerekir.<br><br>Microsoft Yönetilen Masaüstü'ne kaydolmak gerekli değildir, ancak aşağıdaki hizmetlerin buluta geçişlerini kesinlikle öneririz:<ul><li>E-posta: Bulut tabanlı posta kutularına Exchange, çevrimiçi olabilir veya Exchange Online 2013 veya daha yüksek bir Exchange ile şirket içi Karma ile yapılandırabilirsiniz.</li><li>Dosyalar ve klasörler: OneDrive İş Veya SharePoint Online'a geçiş.</li><li>Çevrimiçi işbirliği araçları: Diğer araçlara Teams.</ul> |
| Cihaz yönetimi | Microsoft Yönetilen Masaüstü cihazları için yönetim, yönetim Microsoft Intune. Intune,Mobil Cihaz Yönetimi yetkilisi olarak ayarlanıyor olmalı.<br><br> Daha fazla bilgi için bkz. [Microsoft Intune](https://www.microsoft.com/cloud-platform/microsoft-intune).
| Veri yedekleme ve kurtarma | Microsoft Yönetilen Masaüstü, dosyaların koruma için bilgisayarınıza eşit OneDrive İş gerektirir. Bu dosyalarla eşitlenen OneDrive İş Microsoft Yönetilen Masaüstü tarafından garanti edilemez. Cihaz değişimleri veya cihaz sıfırlamayı gerektiren destek aramaları sırasında dosyalar kaybolabilir.<br><br>Microsoft Yönetilen Masaüstü, gerekli olsa da eşlenmiş ağ sürücülerinden uygun bulut çözümüne geçiş önerilen bir uygulamadır. Daha fazla bilgi için bkz [. Eşlenmiş sürücüleri Microsoft Yönetilen Masaüstü için hazırlama](mapped-drives.md)

Microsoft Yönetilen Masaüstü ile çalışmaya başlamaya hazırsanız, Microsoft Hesap Yöneticinizle iletişime geçin.

## <a name="more-about-licenses"></a>Lisanslar hakkında daha fazla bilgi

Microsoft Yönetilen Masaüstü'nin çalışması için bazı lisans seçenekleri gerekir. Bu [lisansların nasıl kullanıldıkları](../intro/technologies.md) hakkında bilgi için bkz. Microsoft Yönetilen Masaüstü teknolojileri.

> [!TIP]
> Bu lisans seçeneklerini belirli kullanıcılara atamak için, kullanıcıların grup tabanlı lisanslama [özelliğiden yararlanmalarını](/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal) Azure Active Directory.

- Azure Active Directory Premium P1
- Microsoft Intune
- Windows 10 Enterprise  
- Uç Nokta için Microsoft Defender
- Microsoft 365 Kurumsal Uygulamaları
- Microsoft Teams
- [SharePoint Online Plan 2](https://www.microsoft.com/microsoft-365/sharepoint/compare-sharepoint-plans)
- [Exchange Online Plan 2](https://www.microsoft.com/microsoft-365/exchange/compare-microsoft-exchange-online-plans)

> [!TIP]
> Microsoft Hesap Yöneticiniz, çoğaltmayı önlerken geçerli lisanslarınızı, hizmet planlarınızı gözden geçirmenize ve ihtiyacınız olan ek lisansları veya hizmet planlarını alamanız için en verimli yolu bulamanıza yardımcı olur.

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Microsoft Yönetilen Masaüstü için hazır adımlar

1. Önkoşulları gözden geçir (bu makale).
1. Hazırlık [değerlendirme araçlarını çalıştırın](readiness-assessment-tool.md).
1. Satın [Şirket Portalı](../get-started/company-portal.md).
1. Konuk [hesapları için önkoşulları gözden geçirebilirsiniz](guest-accounts.md).
1. Ağ [yapılandırmasını denetleme](network.md).
1. [Sertifikaları ve ağ profillerini hazırlayın](certs-wifi-lan.md).
1. [Verileri kullanıcı erişimini hazırlama](authentication.md).
1. [Uygulamaları hazırlama](apps.md).
1. [Eşlenmiş sürücüleri hazırlama](mapped-drives.md).
1. [Yazdırma kaynaklarını hazırlama](printing.md).
1. Cihaz [adlarını adresle](address-device-names.md).
