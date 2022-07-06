---
title: Hizmet şifrelemesi
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.date: 10/3/2019
ms.localizationpriority: ''
search.appverid:
- MET150
ms.collection: Strat_O365_Enterprise
description: 'Özet: Microsoft Office 365 veri dayanıklılığını anlama.'
ms.openlocfilehash: 66899a337e9349a78178df67aa83e44b580c7148
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629389"
---
# <a name="service-encryption"></a>Hizmet Şifrelemesi

Birim düzeyinde şifrelemenin yanı sıra Exchange Online, Microsoft Teams, SharePoint Online ve OneDrive İş de müşteri verilerini şifrelemek için Hizmet Şifrelemesi'ni kullanır. Hizmet Şifrelemesi iki anahtar yönetimi seçeneğine olanak tanır:

## <a name="microsoft-managed-keys"></a>Microsoft tarafından yönetilen anahtarlar
Microsoft, hizmet şifrelemesi için kök anahtarlar da dahil olmak üzere tüm şifreleme anahtarlarını yönetir. Bu seçenek şu anda Exchange Online, SharePoint Online OneDrive İş için varsayılan olarak etkindir. Microsoft tarafından yönetilen anahtarlar, Müşteri Anahtarı'nı kullanmaya karar vermediğiniz sürece varsayılan hizmet şifrelemesi sağlar. Daha sonraki bir tarihte veri temizleme yolunu izlemeden Müşteri Anahtarı'nı kullanmayı durdurmaya karar verirseniz verileriniz Microsoft tarafından yönetilen anahtarlar kullanılarak şifrelenir. Verileriniz her zaman en az bu varsayılan düzeyde şifrelenir. 

## <a name="customer-key"></a>Müşteri Anahtarı
Hizmet şifrelemesi ile kullanılan kök anahtarları tedarik eder ve bu anahtarları Azure Key Vault kullanarak yönetirsiniz. Microsoft diğer tüm anahtarları yönetir. Bu seçenek Müşteri Anahtarı olarak adlandırılır ve şu anda Exchange Online, SharePoint Online ve OneDrive İş için kullanılabilir. (Daha önce BYOK ile Gelişmiş Şifreleme olarak adlandırılır. Özgün duyuru için bkz[. Office 365 müşterileri için saydamlığı ve denetimi geliştirme](https://www.microsoft.com/en-us/microsoft-365/blog/2015/04/21/enhancing-transparency-and-control-for-office-365-customers/).)

Hizmet şifrelemesi birden çok avantaj sağlar:

- BitLocker'ın üzerine ek bir koruma katmanı sağlar.

- Windows işletim sistemi yöneticilerinin, işletim sistemi tarafından depolanan veya işlenen uygulama verilerine erişimden ayrılmasını sağlar.

- Çok kiracılı hizmetlerin kiracı başına anahtar yönetimi sağlamasını sağlayan bir Müşteri Anahtarı seçeneği içerir.

- Microsoft 365'in şifrelemeyle ilgili belirli uyumluluk gereksinimlerine sahip müşterilerin taleplerini karşılama becerisini geliştirir.

Müşteri Anahtarı'nı kullanarak, şirket içi Donanım Hizmeti Modülü (HSM) veya Azure Key Vault (AKV) kullanarak kendi şifreleme anahtarlarınızı oluşturabilirsiniz. Anahtarı nasıl oluşturduğunuzdan bağımsız olarak, Office 365 tarafından kullanılan şifreleme anahtarlarını denetlemek ve yönetmek için AKV kullanırsınız. Anahtarlarınız AKV'de depolandıktan sonra, posta kutusu verilerinizi veya dosyalarınızı şifreleyen anahtarlıklardan birinin kökü olarak kullanılabilir.

Müşteri Anahtarı'nın bir diğer avantajı da Microsoft'un verilerinizi işleme yeteneği üzerinde sahip olduğunuz denetimdir. Microsoft ile hizmeti sonlandırmak veya bulutta depolanan verilerinizin bir bölümünü kaldırmak gibi verileri Office 365 kaldırmak istiyorsanız, bunu yapabilir ve teknik denetim olarak Müşteri Anahtarı'nı kullanabilirsiniz. Verilerin kaldırılması, Microsoft da dahil olmak üzere hiç kimsenin verilere erişemesini veya verileri işleyebilmesini sağlar. Müşteri Anahtarı, Microsoft personeli tarafından verilerinize erişimi denetlemek için kullandığınız Müşteri Kasası'na ek ve tamamlayıcıdır.

Ekip Siteleri ve OneDrive İş dahil olmak üzere Exchange Online, Microsoft Teams, SharePoint Online için Microsoft 365 Müşteri Anahtarını ayarlamayı öğrenmek için şu makalelere bakın:

- [Müşteri Anahtarı ile hizmet şifrelemesi](customer-key-overview.md)

- [Müşteri Anahtarını Ayarlama](customer-key-set-up.md)

- [Müşteri Anahtarını Yönet](customer-key-manage.md)

- [Müşteri anahtarını veya kullanılabilirlik anahtarını alma veya döndürme](customer-key-availability-key-roll.md)

- [Kullanılabilirlik anahtarını anlama](customer-key-availability-key-understand.md)
