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
description: Bu makalede, Microsoft bulutunda müşteri verilerini güvende tutmak için kullanılan çeşitli şifreleme biçimlerine genel bir bakış bulabilirsiniz.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: c888c1958eb5265c31ae981e42a96eeeeb57f3ef
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988087"
---
# <a name="encryption-in-the-microsoft-cloud"></a>Microsoft Bulut'ta şifreleme

Microsoft'un kurumsal bulut hizmetleri içindeki müşteri verileri çeşitli şifreleme formları da dahil olmak üzere çeşitli teknolojiler ve süreçler tarafından korunur. (Bu belgedeki müşteri verileri Exchange Online posta kutusu içeriği, e-posta gövdesi, takvim girdileri ve e-posta eklerinin içeriği, varsa Skype Kurumsal içeriği), SharePoint Online site içeriği ve siteler içinde depolanan dosyalar ve OneDrive İş veya Skype Kurumsal.) Microsoft, ürün ve hizmetleri genelinde birden çok şifreleme yöntemi, protokol ve şifreleme kullanarak, müşteri verileri için bulut hizmetlerimizde seyahat etmek üzere güvenli bir yol sağlamaya ve bulut hizmetlerimizde depolanan müşteri verilerinizin gizliliğini korumaya yardımcı olur. Microsoft, müşteri verilerine yetkisiz erişim engellerini sağlamak için mevcut olan en güçlü ve en güvenli şifreleme protokollerinden bazılarını kullanır. Doğru anahtar yönetimi de en iyi şifreleme en iyi yöntemlerinin temel öğesidir ve Microsoft tarafından yönetilen tüm şifreleme anahtarlarının düzgün güvenliğini sağlamaya çalışır.

Microsoft'un kurumsal bulut hizmetleri içinde depolanan müşteri verileri, bir veya daha fazla şifreleme formu kullanılarak korunur. (Şifreleme ilkemizin ve uygulamanın doğrulaması, birden çok üçüncü taraf denetçi tarafından bağımsız olarak doğrulanır ve bu denetimlerin raporları Hizmet Güveni [Portalı'nda mevcuttur](https://aka.ms/stp).)

Microsoft, müşteri verilerini istiraden ve iletilirken şifrelenen hizmet tarafı teknolojileri sunar. Örneğin, beklemede müşteri verileri için Microsoft Azure [BitLocker](/windows/device-security/bitlocker/bitlocker-overview) ve [DM-Crypt](https://en.wikipedia.org/wiki/Dm-crypt) kullanır ve Microsoft 365'de BitLocker, [Azure Depolama Hizmet](/azure/) Şifrelemesi, [Dağıtılmış](./exchange-online-secures-email-secrets.md) Anahtar Yöneticisi (DKM) ve Microsoft 365 şifrelemesi kullanılır. İletim halindeki müşteri verileri için Azure, Office 365, Microsoft Ticari Desteği, Microsoft Dynamics 365, Microsoft Power BI ve Visual Studio Team Services İnternet Protokolü Güvenliği (I Aygıtlar) ve Aktarım Katmanı Güvenliği (TLS) gibi, Microsoft veri merkezleri arasında ve kullanıcı cihazları arasında endüstri standardı güvenli aktarım protokollerini kullanır ve Microsoft veri merkezleri.

Microsoft tarafından sağlanan şifreleme güvenliği taban çizgisi düzeyine ek olarak, bulut hizmetlerimiz yönetebilirsiniz şifreleme seçeneklerini de içerir. Örneğin, Azure sanal makineleri (SANAL MAKINELERI) ve kullanıcıları arasındaki trafiğin şifrelemesini etkinleştirebilirsiniz. [Azure Sanal Ağlarında](https://azure.microsoft.com/services/virtual-network/), endüstri standardı I İleti protokolünü kullanarak şirket VPN ağ geçidiniz ve Azure arasındaki trafiği şifreebilirsiniz. Ayrıca, sanal ağ ağınız üzerinden de sanal makineler arasındaki trafiği şifreebilirsiniz. Buna ek [olarak, Office 365 İleti Şifrelemesi özellikleri](set-up-new-message-encryption-capabilities.md) herkese şifreli posta göndermenizi sağlar.

[Microsoft](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=5868ecc8-50b7-4f91-b43f-640e2b99e86e&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ%20and%20White%20Papers) Güvenlik İlkesi'nin bir bileşeni olan Ortak Anahtar Altyapısı İşlem Güvenlik Standardı'nın ardından, sertifikalar ve kimlik doğrulama mekanizmaları için Windows işletim sisteminde bulunan şifreleme özelliklerini kullanır. Bu mekanizmalar, ABD hükümetinin [Federal](https://csrc.nist.gov/publications/PubsFIPS.html) Bilgi İşleme Standartları (FIPS) 140-2 standardını karşılayacak şifreleme modüllerinin kullanımını içerir. Şifreleme Modülü Doğrulama Programı CMVP'sını kullanarak Microsoft için ilgili NIST [sertifika numaralarını arayabilirsiniz](https://csrc.nist.gov/projects/cryptographic-module-validation-program/validated-modules/search).

> [NOT] Kaynak olarak Microsoft Güvenlik İlkesi'ne erişmek için iş veya okul hesabınızla oturum açın. Henüz bir aboneliğiniz yoksa, [ücretsiz deneme için kaydolabilirsiniz](https://servicetrust.microsoft.com/Home/TrialSubscriptions).

FIPS 140-2, bunları kullanan ürünler yerine şifreleme uygulayan ürün modüllerinin doğrulanacak şekilde özel olarak tasarlanmış bir standarttır. Bir hizmette uygulanan şifreleme modülleri karma gücü, anahtar yönetimi ve benzerleri gereksinimlerini karşılamak için sertifikalı olabilir. Microsoft'un bulut hizmetlerde verilerin gizliliğini, bütünlüğünü ve kullanılabilirliğini korumak için kullanılan şifreleme modülleri ve şifrelemeler FIPS 140-2 standardını karşılar.

Microsoft, bulut hizmetlerimizde kullanılan temel şifreleme modüllerini, bulut işletim sisteminin her yeni sürümüyle Windows sağlar:

- Azure ve Azure U.S. Government
- Dynamics 365 ve Dynamics 365 ABD Kamu
- Office 365, Office 365.s. Government, and Office 365 U.S. Government Savunma

Beklemede müşteri verilerini şifreleme bitLocker, DKM, Azure Depolama Hizmet Şifrelemesi ve Exchange Online, Skype Kurumsal, OneDrive İş ve SharePoint Online'da hizmet şifreleme dahil olmak üzere birden çok hizmet tarafı teknolojisi tarafından sağlanır. Office 365 şifreleme, Azure Anahtar Kasasında depolanan müşteri tarafından yönetilen şifreleme anahtarlarını kullanma seçeneği içerir. Müşteri Anahtarı adı verilen bu müşteri tarafından yönetilen anahtar [seçeneği, Exchange Online](./customer-key-overview.md), SharePoint Online, Skype Kurumsal ve OneDrive İş.

Geçişteki müşteri verileri için tüm Office 365 sunucuları, müşteri verilerini güvence altına almak için varsayılan olarak ISTEMCI makineleriyle TLS kullanarak güvenli oturumlar sağlar. Örneğin, Office 365, mobil istemciler ve web tarayıcıları Skype Kurumsal Outlook ve Web üzerinde Outlook oturumları yapmak için güvenli oturumlar yapmaya devam edecek.

(Varsayılan olarak, müşteriye yönelik tüm sunucular TLS 1.2 üzerinde anlaşmalar sağlar.)

## <a name="related-links"></a>İlgili Bağlantılar

- [Azure'da şifreleme](office-365-azure-encryption.md)
- [Şifreleme için BitLocker ve Dağıtılmış Anahtar Yöneticisi (DKM)](office-365-bitlocker-and-distributed-key-manager-for-encryption.md)
- [Office 365 Hizmeti Şifrelemesi](office-365-service-encryption.md)
- [Office 365, Skype Kurumsal, OneDrive İş, SharePoint Online ve Exchange Online için Şifreleme](/compliance/assurance/assurance-encryption-for-microsoft-365-services) 
- [Toplu Taşımadaki Veriler için Şifreleme](/compliance/assurance/assurance-encryption-in-transit)
- [Müşteri Tarafından Yönetilen Şifreleme Özellikleri](office-365-customer-managed-encryption-features.md)
- [Şifreleme Riskleri ve Korumalar](office-365-encryption-risks-and-protections.md)
- [Microsoft Dynamics 365'te şifreleme](office-365-encryption-in-microsoft-dynamics-365.md)