---
title: Etki Alanı Bağlan kullanma
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
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
description: Etki alanı Bağlan etkin kayıt şirketleri ile çalışmayı ve etki alanınızı Microsoft 365 eklemeyi öğrenin.
ms.openlocfilehash: e20588181a5e9ca55d11844e2f31c3504a2bbfa0
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65437623"
---
# <a name="using-domain-connect-to-add-your-domain-to-microsoft-365"></a>Etki alanınızı Microsoft 365 eklemek için Etki Alanı Bağlan kullanma

 Aradığınızı bulamazsanız, **[Etki Alanları SSS sayfasını inceleyin](../setup/domains-faq.yml)**.

[Etki alanı Bağlan](https://www.domainconnect.org/) etkin kayıt şirketleri, dakikalar süren üç adımlı bir işlemle etki alanınızı Microsoft 365 eklemenize olanak sağlar.

Sihirbazda yalnızca etki alanının sahibi olduğunuzu onaylayacak ve ardından etki alanınızın kayıtlarını otomatik olarak ayarlayacağız, bu nedenle e-posta Microsoft 365 ve Teams gibi diğer Microsoft 365 hizmetlerine gelir ve etki alanınızla çalışır.

> [!NOTE]
> Kurulum sihirbazını başlatmadan önce tarayıcınızda tüm açılır pencere engelleyicilerini devre dışı bırakın.

## <a name="domain-connect-registrars-integrating-with-microsoft-365"></a>Microsoft 365 ile tümleştiren etki alanı Bağlan kayıt şirketleri

- [11&amp; IONOS](https://www.1and1.com/)
- [123Bölge](https://www.123-reg.co.uk/)
- [Godaddy](https://www.godaddy.com/)
- [Wordpress](https://wordpress.com/)
- [Plesk](https://www.plesk.com/)
- [MediaTemple](https://mediatemple.net/)
- SecureServer veya WildWestDomains (SecureServer DNS barındırma kullanan GoDaddy kurumsal bayileri)
  - [MadDog Web Barındırma](https://maddogwebhosting.com/domains/)
  - [CheapNames](https://www.cheapnames.com)

## <a name="what-happens-to-my-email-and-website"></a>E-postama ve web siteme ne olur?

Kurulumu tamamladıktan sonra, etki alanınızın MX kaydı Microsoft 365 işaret edecek şekilde güncelleştirilir ve etki alanınızın tüm e-postaları Microsoft 365 gelmeye başlar. Etki alanınızda e-posta alan herkes için kullanıcıları eklediğinizden ve posta kutularını Microsoft 365 ayarladığınızdan emin olun!

İş için kullandığınız bir web siteniz varsa, bu site bulunduğu yerde çalışmaya devam eder. Etki alanı Bağlan kurulum adımları web sitenizi etkilemez.
