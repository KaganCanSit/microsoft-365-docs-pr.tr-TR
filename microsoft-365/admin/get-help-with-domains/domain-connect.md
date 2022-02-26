---
title: Etki Alanı Denetleyicisi'Bağlan
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_O365_Setup
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: ec6f4bd8-5996-4505-ba68-afaf8a141fb9
description: Etkin olan etki alanı kayıt Bağlan etki alanı kayıt siteleriyle nasıl çalış ve etki Microsoft 365.
ms.openlocfilehash: 6203292332d895d99131c4ab324fc342da9aaeed
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973598"
---
# <a name="using-domain-connect"></a>Etki Alanı Denetleyicisi'Bağlan

 Aradığınızı bulamazsanız, **[Etki Alanları SSS sayfasını inceleyin](../setup/domains-faq.yml)**.

[Etki Bağlan](https://www.domainconnect.org/) kayıt adları, dakikalar geçen üç adımlık bir Microsoft 365 etki alanınıza etki alanı eklemenize izin sağlar.

Sihirbazda, etki alanının sahibi olduğunu doğrular ve ardından e-postanın Microsoft 365'a ve Teams gibi diğer Microsoft 365 hizmetleriyle birlikte etki alanınıza çalışması için etki alanı kayıtlarınız otomatik olarak ayarlanır.

> [!NOTE]
> Kurulum sihirbazını başlatmadan önce tarayıcınızda tüm açılır pencere engelleyicilerini devre dışı bırakın.

## <a name="domain-connect-registrars-integrating-with-microsoft-365"></a>Etki Bağlan kayıt şirketleriyle tümleştirmesi Microsoft 365

- [11&amp; IONOS](https://www.1and1.com/)
- [123Reg](https://www.123-reg.co.uk/)
- [GoDaddy](https://www.godaddy.com/)
- [WordPress](https://wordpress.com/)
- [Tiryak](https://www.plesk.com/)
- [MediaTemple](https://mediatemple.net/)
- SecureServer veya WildWestDomains (SecureServer DNS barındırmayı kullanan GoDaddy satıcıları)
  - [MadDog Web Hosting](https://maddogwebhosting.com/domains/)
  - [CheapNames](https://www.cheapnames.com)

## <a name="what-happens-to-my-email-and-website"></a>E-postama ve web siteme ne olur?

Kurulumu bitirdikten sonra, etki alanınıza göre MX kaydı Microsoft 365'a işaret etmek üzere güncelleştirilir ve etki alanınıza gelen tüm e-posta bu adrese Microsoft 365. Kullanıcıları ekleyenin ve etki alanınıza e-posta Microsoft 365 herkes için posta kutularını bu e-posta kutusunda ayarlayın!

İş için kullandığınız bir web siteniz varsa, bu site bulunduğu yerde çalışmaya devam eder. Etki Bağlan kurulum adımları web sitenizi etkilemez.
