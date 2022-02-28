---
title: Hizmet Şifrelemesi
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
description: 'Özet: Verinin daha iyi bir şekilde Microsoft Office 365.'
ms.openlocfilehash: b83b55afab2d9901e03a311d603b5b316531580a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983486"
---
# <a name="service-encryption"></a>Hizmet Şifrelemesi

Toplu şifrelemenin yanı sıra, Exchange Online, Microsoft Teams, SharePoint Online ve OneDrive İş da müşteri verilerini şifrelemek için Hizmet Şifrelemesi'ne sahip olur. Hizmet Şifrelemesi iki temel yönetim seçeneğine olanak sağlar:

## <a name="microsoft-managed-keys"></a>Microsoft tarafından yönetilen anahtarlar
Microsoft, hizmet şifrelemesi için kök anahtarlar da dahil olmak üzere tüm şifreleme anahtarlarını yönetir. Bu seçenek şu anda Exchange Online Online ve SharePoint için varsayılan olarak OneDrive İş. Müşteri Anahtarı'nın kullanımına eklemeye karar vermedikçe, Microsoft tarafından yönetilen anahtarlar varsayılan hizmet şifrelemesi sağlar. Daha sonraki bir tarihte, veri temizleme yolunu takip etmeden Müşteri Anahtarı'nın kullanımına son vermenizi sağlarsanız, Microsoft tarafından yönetilen anahtarlar kullanılarak verileriniz şifrelenmiş olarak kalır. Verileriniz en azından bu varsayılan düzeyde her zaman şifrelenir. 

## <a name="customer-key"></a>Müşteri Anahtarı
Hizmet şifrelemesi ile kullanılan kök anahtarları sağlar ve bu anahtarları Azure Anahtar Kasasını kullanarak yönetirsiniz. Microsoft diğer tüm anahtarları yönetir. Bu seçenek Müşteri Anahtarı olarak adlandırılan bu seçenek, şu anda Exchange Online, SharePoint Online ve OneDrive İş. (Daha önce BYOK ile Gelişmiş Şifreleme olarak adlandırılır. Bkz[. İlk duyuru için Office 365 saydamlık](https://blogs.office.com/2015/04/21/enhancing-transparency-and-control-for-office-365-customers/) ve denetimi geliştirme.)

Hizmet şifreleme çeşitli avantajlar sağlar:

- BitLocker'ın üzerine ek bir koruma katmanı sağlar.

- İşletim sistemi Windows, işletim sistemi tarafından depolanan veya işlenen uygulama verilerine erişimden ayrım sağlar.

- Çok kiracılı hizmetlerin kiracı başına anahtar yönetimini sağlamasına olanak sağlayan bir Müşteri Anahtarı seçeneği vardır.

- Şifrelemeyle ilgili belirli Microsoft 365 gereksinimleri olan müşterilerin taleplerini karşılama olanağını geliştirmektedir.

Müşteri Anahtarı'nın kullanımı, şirket içi Donanım Hizmet Modülü(HSM) veya Azure Anahtar Kasası'nın (AKV) kullanımıyla kendi şifreleme anahtarlarınızı oluşturmanızı sağlar. Anahtarı nasıl oluştur olur da olur da, GÜVENLIK tarafından kullanılan şifreleme anahtarlarını kontrol etmek ve yönetmek için AKV Office 365. Anahtarlarınız AKV'de depolandığı anda, posta kutusu verilerinizi veya dosyalarınızı şifrelenen anahtar anahtarlıklardan birinin kökü olarak kullanılabilir.

Müşteri Anahtarı'nın bir diğer avantajı, Microsoft'un verilerinizi işlemesi üzerinde sahip olduğunuz denetimdir. Office 365'tan verileri kaldırmak, örneğin Hizmeti Microsoft'la sonlandırmak veya verilerinizin bulutta depolanan bir bölümünü kaldırmak gibi durumlarda, bunu yapmak ve Müşteri Anahtarını teknik denetim olarak kullanmaktır. Verileri kaldırma işlemi, Microsoft dahil hiç kimsenin verilere erişmelerini veya verileri işlemelerini sağlar. Müşteri Anahtarı, Microsoft personeli tarafından verilerinize erişiminizi kontrol etmek için kullanabileceğiniz Müşteri Kilidine ek ve tamamlayıcı niteliktedir.

Ekip Siteleri ve diğer web siteleri dahil Microsoft 365 Exchange Online, Microsoft Teams, SharePoint Online için Müşteri Anahtarını ayarlamayı OneDrive İş için şu makalelere bakın:

- [Müşteri Anahtarı ile Hizmet şifrelemesi](customer-key-overview.md)

- [Müşteri Anahtarını Ayarlama](customer-key-set-up.md)

- [Müşteri Anahtarını Yönet](customer-key-manage.md)

- [Müşteri anahtarını veya uygunluk anahtarını döndürme veya döndürme](customer-key-availability-key-roll.md)

- [Kullanılabilirlik anahtarını anlama](customer-key-availability-key-understand.md)
