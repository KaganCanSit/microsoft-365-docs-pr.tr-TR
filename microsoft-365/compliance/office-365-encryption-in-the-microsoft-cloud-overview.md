---
title: Microsoft Bulut'ta şifreleme
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
search.appverid:
- MET150
ms.collection:
- Strat_O365_Enterprise
- M365-security-compliance
- Strat_O365_Enterprise
description: Bu makalede, müşteri verilerini Microsoft bulutunda güvende tutmak için kullanılan çeşitli şifreleme biçimlerine genel bir bakış okuyun.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 3105da5d17b1656ffa0d29da4f4aa02c9a9f9064
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66633927"
---
# <a name="encryption-in-the-microsoft-cloud"></a>Microsoft Bulut'ta şifreleme

Microsoft'un kurumsal bulut hizmetlerindeki müşteri verileri, çeşitli şifreleme biçimleri de dahil olmak üzere çeşitli teknoloji ve süreçlerle korunur. (Bu belgedeki müşteri verileri Exchange Online posta kutusu içeriğini, e-posta gövdesini, takvim girdilerini ve e-posta eklerinin içeriğini ve varsa Skype Kurumsal içeriği), SharePoint Online site içeriğini ve sitelerde depolanan dosyaları ve OneDrive İş veya Skype Kurumsal'a yüklenen dosyaları içerir .) Microsoft, müşteri verilerinin bulut hizmetlerimiz üzerinden ilerlemesi için güvenli bir yol sağlamaya yardımcı olmak ve bulut hizmetlerimizde depolanan müşteri verilerinin gizliliğini korumaya yardımcı olmak için ürün ve hizmetleri genelinde birden çok şifreleme yöntemi, protokol ve şifreleme kullanır. Microsoft, müşteri verilerine yetkisiz erişime karşı engel sağlamak için en güçlü, en güvenli şifreleme protokollerinden bazılarını kullanır. Düzgün anahtar yönetimi aynı zamanda en iyi şifreleme yöntemlerinin önemli bir öğesidir ve Microsoft, Microsoft tarafından yönetilen tüm şifreleme anahtarlarının düzgün bir şekilde korunmasını sağlamak için çalışır.

Microsoft'un kurumsal bulut hizmetlerinde depolanan müşteri verileri bir veya daha fazla şifreleme biçimi kullanılarak korunur. (Şifreleme politikamızın ve uygulanmasının doğrulanması, birden çok üçüncü taraf denetçi tarafından bağımsız olarak doğrulanır ve bu denetimlerin raporları [Hizmet Güveni Portalı'nda](https://aka.ms/stp) sağlanır.)

Microsoft bekleyen ve aktarımdaki müşteri verilerini şifreleyen hizmet tarafı teknolojileri sağlar. Örneğin, bekleyen müşteri verileri için Microsoft Azure BitLocker ve [DM-Crypt](https://en.wikipedia.org/wiki/Dm-crypt), Microsoft 365 ise [BitLocker](/windows/device-security/bitlocker/bitlocker-overview), [Azure Depolama Hizmeti Şifrelemesi](/azure/), [Dağıtılmış Anahtar Yöneticisi](./exchange-online-secures-email-secrets.md) (DKM) ve Microsoft 365 hizmet şifrelemesi kullanır. Aktarımdaki müşteri verileri için Azure, Office 365, Microsoft Ticari Destek, Microsoft Dynamics 365, Microsoft Power BI ve Visual Studio Team Services, Microsoft veri merkezleri arasında ve kullanıcı cihazları ile Microsoft veri merkezleri arasında İnternet Protokolü Güvenliği (IPsec) ve Aktarım Katmanı Güvenliği (TLS) gibi endüstri standardı güvenli aktarım protokollerini kullanır.

Bulut hizmetlerimiz, Microsoft tarafından sağlanan şifreleme güvenliğinin temel düzeyine ek olarak yönetebileceğiniz şifreleme seçeneklerini de içerir. Örneğin, Azure sanal makineleri (VM' ler) ile kullanıcıları arasındaki trafik için şifrelemeyi etkinleştirebilirsiniz. [Azure Sanal Ağlar](https://azure.microsoft.com/services/virtual-network/) ile kurumsal VPN ağ geçidiniz ile Azure arasındaki trafiği şifrelemek için endüstri standardı IPsec protokollerini kullanabilirsiniz. Sanal ağınızdaki VM'ler arasındaki trafiği de şifreleyebilirsiniz. Ayrıca[, yeni Office 365 İleti Şifreleme özellikleri](set-up-new-message-encryption-capabilities.md), herkese şifreli posta göndermenizi sağlar.

Microsoft Güvenlik İlkesi'nin bir bileşeni olan Ortak Anahtar Altyapısı [İşletimSelsel Güvenlik](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=5868ecc8-50b7-4f91-b43f-640e2b99e86e&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ%20and%20White%20Papers) Standardı'nı izleyen Microsoft, sertifikalar ve kimlik doğrulama mekanizmaları için Windows işletim sistemine dahil olan şifreleme özelliklerini kullanır. Bu mekanizmalar, ABD hükümetinin [Federal Bilgi İşleme Standartları](https://csrc.nist.gov/publications/PubsFIPS.html) (FIPS) 140-2 standardını karşılayan şifreleme modüllerinin kullanımını içerir. [Şifreleme Modülü Doğrulama Programı CMVP'sini](https://csrc.nist.gov/projects/cryptographic-module-validation-program/validated-modules/search) kullanarak Microsoft için ilgili NIST sertifika numaralarını arayabilirsiniz.

> [NOT] Microsoft Güvenlik İlkesi'ne kaynak olarak erişmek için iş veya okul hesabınızı kullanarak oturum açmanız gerekir. Henüz bir aboneliğiniz yoksa [ücretsiz deneme için kaydolabilirsiniz](https://servicetrust.microsoft.com/Home/TrialSubscriptions).

FIPS 140-2, bunları kullanan ürünler yerine şifreleme uygulayan ürün modüllerini doğrulamak için özel olarak tasarlanmış bir standarttır. Bir hizmet içinde uygulanan şifreleme modülleri karma gücü, anahtar yönetimi ve benzeri gereksinimleri karşılıyor olarak sertifikalanabilir. Microsoft'un bulut hizmetlerindeki verilerin gizliliğini, bütünlüğünü veya kullanılabilirliğini korumak için kullanılan şifreleme modülleri ve şifreleri FIPS 140-2 standardını karşılar.

Microsoft, bulut hizmetlerimizde kullanılan temel şifreleme modüllerini Windows işletim sisteminin her yeni sürümüyle onaylar:

- Azure ve Azure ABD Kamu
- Dynamics 365 ve Dynamics 365 ABD Hükümeti
- Office 365, ABD Hükümeti Office 365 ve abd kamu savunmasını Office 365

Bekleyen müşteri verilerinin şifrelenmesi, BitLocker, DKM, Azure Depolama Hizmeti Şifrelemesi ve Exchange Online, Skype Kurumsal, OneDrive İş ve SharePoint Online'da hizmet şifrelemesi gibi birden çok hizmet tarafı teknolojisi tarafından sağlanır. Office 365 hizmet şifrelemesi, Azure Key Vault'da depolanan müşteri tarafından yönetilen şifreleme anahtarlarını kullanma seçeneği içerir. [Müşteri Anahtarı](./customer-key-overview.md) olarak adlandırılan bu müşteri tarafından yönetilen anahtar seçeneği Exchange Online, SharePoint Online, Skype Kurumsal ve OneDrive İş için kullanılabilir.

Aktarımdaki müşteri verileri için tüm Office 365 sunucuları, müşteri verilerinin güvenliğini sağlamak için varsayılan olarak TLS kullanarak güvenli oturumlar oluşturur. Örneğin, Office 365 Skype Kurumsal, Outlook ve Web üzerinde Outlook, mobil istemciler ve web tarayıcıları için güvenli oturumlar anlaşması yapacaktır.

(Müşteriye yönelik tüm sunucular varsayılan olarak TLS 1.2 ile anlaşma sağlar.)

## <a name="related-links"></a>İlgili Bağlantılar

- [Azure'da şifreleme](office-365-azure-encryption.md)
- [Şifreleme için BitLocker ve Dağıtılmış Anahtar Yöneticisi (DKM)](office-365-bitlocker-and-distributed-key-manager-for-encryption.md)
- [Office 365 Hizmet Şifrelemesi](office-365-service-encryption.md)
- [Skype Kurumsal, OneDrive İş, SharePoint Online ve Exchange Online için Office 365 Şifrelemesi](/compliance/assurance/assurance-encryption-for-microsoft-365-services) 
- [Aktarımdaki Veriler için Şifreleme](/compliance/assurance/assurance-encryption-in-transit)
- [Müşteri Tarafından Yönetilen Şifreleme Özellikleri](office-365-customer-managed-encryption-features.md)
- [Şifreleme Riskleri ve Korumaları](office-365-encryption-risks-and-protections.md)
- [Microsoft Dynamics 365'te şifreleme](office-365-encryption-in-microsoft-dynamics-365.md)
