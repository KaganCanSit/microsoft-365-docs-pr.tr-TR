---
title: Microsoft Yönetilen Masaüstü için sertifikaları ve ağ profillerini hazırlama
description: Sertifika gereksinimleri ve wi-fi bağlantısı
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: ccdd9f390c794590eed6cbe11d169430f92bdf55
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/10/2022
ms.locfileid: "63027579"
---
# <a name="prepare-certificates-and-network-profiles-for-microsoft-managed-desktop"></a>Microsoft Yönetilen Masaüstü için sertifikaları ve ağ profillerini hazırlama  

Sertifika tabanlı kimlik doğrulama, Microsoft Yönetilen Masaüstü kullanan müşteriler için yaygın bir gereksinimdir. Şunları yapmak için sertifika gerekli olabilir:

- E-Wi-Fi LAN'ye erişim
- Bağlan VPN çözümlerine bağlantı
- Kurum içinde iç kaynaklara erişme

Microsoft Yönetilen Masaüstü cihazları Azure Active Directory'a (Azure AD) katıldığı ve Microsoft Intune tarafından yönetiller olduğundan, bu tür sertifikaları aşağıdakini kullanarak dağıtmanız gerekir:

- Basit Sertifika Kaydı Protokolü (SCEP) veya
- Intune ile tümleşik olan Ortak Anahtar Şifreleme Standardı (PKCS) sertifika altyapısı.

## <a name="certificate-requirements"></a>Sertifika gereksinimleri

Kök sertifikalar, sertifikaları SCEP veya PKCS altyapısı aracılığıyla dağıtmak için gereklidir. Microsoft Yönetilen Masaüstü cihazlarınıza dağıtılacak kök sertifikaların kuruma dağıtılmasını gerektiren diğer uygulamalar ve hizmetler olabilir.

SCEP veya PKCS sertifikalarını Microsoft Yönetilen Masaüstü'ne dağıtmadan önce, kurumda kullanıcı veya cihaz sertifikası gerektiren her hizmet için gereksinimleri toplamanız gerekir. Bu etkinliği kolaylaştırmak için aşağıdaki planlama şablonlarından birini kullanabilirsiniz:  

- [PKCS sertifika şablonu](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/managed-desktop/get-ready/downloads/PKCS-certificate-template.xlsx)
- [SCEP sertifika şablonu](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/managed-desktop/get-ready/downloads/SCEP-certificate-template.xlsx)

## <a name="wi-fi-connectivity-requirements"></a>Wi-Fi gereksinimlerini karşıla

Bir cihazın, kuruluş ağınız için gereken ağ yapılandırmasıyla Wi-Fi olarak sağlanıyor olmasına izin vermek için, bir Wi-Fi profili gerekebilir.

Bu profilleri cihazlarınıza dağıtmak için Microsoft Yönetilen Masaüstü'ne yapılandırabilirsiniz. Ağ güvenliğiniz cihazların yerel etki alanının bir parçası olmasını gerektiriyorsa, Microsoft Yönetilen Masaüstü cihazlarıyla uyumlu olduğundan emin olmak için Wi-Fi ağ altyapınızı değerlendirmeniz gerekir. Microsoft Yönetilen Masaüstü cihazları yalnızca Azure AD'ye katıldı.

Microsoft Yönetilen masaüstü Wi-Fi bir yapılandırma dağıtmadan önce, her bir ağ için kuruluş gereksinimlerini toplamanız Wi-Fi gerekir. Bu etkinliği kolaylaştırmak için bu [WiFi profil şablonunu kullanabilirsiniz](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/managed-desktop/get-ready/downloads/WiFi-profile-template.xlsx).

## <a name="wired-connectivity-requirements-and-8021x-authentication"></a>Kablolu bağlantı gereksinimleri ve 802.1x kimlik doğrulaması

Cihazlardan yerel ağınıza (LAN) güvenli erişim için 802.1x kimlik doğrulaması kullanıyorsanız, gerekli yapılandırma ayrıntılarını Microsoft Yönetilen Masaüstü cihazlarınıza basmanız gerekir.

Farklı veya sonraki bir Windows 10, sürüm 1809 çalıştıran Microsoft Yönetilen Masaüstü cihazları, WiredNetwork yapılandırma hizmet sağlayıcısı (CSP) aracılığıyla 802.1x yapılandırmasının dağıtımını destekler. Daha fazla bilgi için [bkz. WiredNetwork CSP](/windows/client-management/mdm/wirednetwork-csp) belgeleri.

Microsoft Yönetilen Masaüstü cihazlarına kablolu bir ağ yapılandırma profili dağıtmadan önce, kablolu şirket ağınız için kurum gereksinimlerinizi toplayın.

**Kablolu şirket ağı gereksinimlerini toplamak için:**

1. Mevcut 802.1x profilinizin yapılandırılmış ve LAN ağına bağlı olduğu bir cihazda oturum açın.  
2. Yönetim kimlik bilgileriyle bir komut istemi açın.
3. çalıştırarak LAN arabiriminin adını bulun `netsh interface show interface`.
4. çalıştırarak LAN profili XML'sini dışarı aktarın `netsh lan export profile folder=.  Interface=”interface_name”`.
5. Dışarı aktarıldı profilinizi Microsoft Yönetilen Masaüstü cihazında test etmek için , çalıştırın `netsh lan add profile filename="PATH_AND_FILENAME.xml" interface="INTERFACE_NAME"`.

## <a name="deploy-certificate-infrastructure"></a>Sertifika altyapısını dağıtma  

Intune ile zaten bir SCEP veya PKCS altyapınız varsa ve bu yaklaşım gereksinimlerinizi karşılarsa, bu altyapıyı Microsoft Yönetilen Masaüstü için de kullanabilirsiniz.

Zaten hiç SCEP veya PKCS altyapısı yoksa, bir tane hazırlamalısiniz. Daha fazla bilgi için bkz[. Mobil cihazlarda cihazlarınız için sertifika Microsoft Intune](/intune/certificates-configure).

## <a name="deploy-a-lan-profile"></a>LAN profilini dağıtma

LAN profiliniz dışarı aktarıldıktan sonra Microsoft Yönetilen Masaüstü için ilke hazırlarız.

**Microsoft Yönetilen Masaüstü ilkesi hazırlamak için:**

1. Aşağıdaki ayarları kullanarak YEREL Microsoft Intune için Yerel Ağ'da özel bir profil oluşturun (bkz[. Intune'daki Windows 10 için özel ayarları kullanma](/intune/custom-settings-windows-10)). Özel **OMA-URI Ayarlar** **Ekle'yi** seçin ve ardından aşağıdaki değerleri girin:
    - Ad: Modern Workplace-Windows 10 LAN Profili
    - Açıklama: Ayara ve diğer önemli ayrıntılara genel bir bakış veren bir açıklama girin.
    - OMA-URI (büyük/harfe duyarlı): Enter `./Device/Vendor/MSFT/WiredNetwork/LanXML`
    - Veri türü: Dize **(XML dosyası) öğesini seçin**.
    - Özel XML: Upload XML dosyasını içerir.
2. Özel profili Modern Çalışma Alanı **Cihazları - Test grubuna** attayın.
3. Test dağıtım grubunda yer alan bir cihaz kullanarak gerekli olduğunu hissedersiniz. Başarılı olursa, özel profili aşağıdaki gruplara attayabilirsiniz:
    - Modern Çalışma Alanı Cihazları - İlk
    - Modern Çalışma Alanı Cihazları - Hızlı
    - Modern Çalışma Alanı Cihazları - Geniş

## <a name="deploy-certificates-and-wi-fivpn-profile"></a>Sertifikaları ve #A0/VPN profilini dağıtma

**Sertifikaları ve profilleri dağıtmak için:**

1. Kök ve Ara sertifikaların her biri için bir profil oluşturun (bkz [. Güvenilir sertifika profilleri oluşturma](/intune/protect/certificates-configure#step-3-create-trusted-certificate-profiles). Bu profillerden her biri, DD/AA/YYYY biçiminde bir son kullanma tarihi içeren bir açıklamaya sahip olmalıdır. **Sertifika profillerinin son kullanma tarihi olmalıdır.**
2. Her SCEP veya PKCS sertifikası için profil oluşturma (bkz. [SCEP](/intune/protect/certificates-scep-configure#create-a-scep-certificate-profile) sertifika profili oluşturma veya [PKCS sertifika profili oluşturma](/intune/protect/certficates-pfx-configure#create-a-pkcs-certificate-profile)). Bu profillerden her biri, DD/AA/YYYY biçiminde bir son kullanma tarihi içeren bir açıklamaya sahip olmalıdır. **Sertifika profillerinin son kullanma tarihi olmalıdır.**
3. Kurumsal WiFi ağların her biri için bir profil oluşturun (bkz. Cihaz ve Windows 10 [Wi-Fi ayarları](/intune/wi-fi-settings-windows)).
4. Şirket VPN'leri için bir profil oluşturun ([Intune kullanarak VPN bağlantıları eklemek Windows 10 ve Holographic Windows ve Holographic cihaz ayarlarına bakın](/intune/vpn-settings-windows-10)).
5. Profilleri Modern Çalışma Alanı Cihazları **- Test grubuna** attayın.
6. Test dağıtım grubunda yer alan bir cihaz kullanarak gerekli olduğunu hissedersiniz. Başarılı olursa, özel profili aşağıdaki gruplara attayabilirsiniz:
    - Modern Çalışma Alanı Cihazları - İlk
    - Modern Çalışma Alanı Cihazları - Hızlı
    - Modern Çalışma Alanı Cihazları - Geniş

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Microsoft Yönetilen Masaüstü için hazır adımlar

1. [Microsoft Yönetilen Masaüstü için önkoşulları gözden geçirebilirsiniz](prerequisites.md).
1. Hazırlık [değerlendirme araçlarını çalıştırın](readiness-assessment-tool.md).
1. Satın [Şirket Portalı](../get-started/company-portal.md).
1. Konuk [hesapları için önkoşulları gözden geçirebilirsiniz](guest-accounts.md).
1. Ağ [yapılandırmasını denetleme](network.md).
1. Sertifikaları ve ağ profillerini hazırlama (bu makale).
1. [Verileri kullanıcı erişimini hazırlama](authentication.md).
1. [Uygulamaları hazırlama](apps.md).
1. [Eşlenmiş sürücüleri hazırlama](mapped-drives.md).
1. [Yazdırma kaynaklarını hazırlama](printing.md).
1. Cihaz [adlarını adresle](address-device-names.md).
