---
title: Bağlan'e Microsoft 365
f1.keywords:
- CSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_O365_Setup
search.appverid:
- MET150
ROBOTS: NOINDEX, NOFOLLOW
description: Etki alanınızı doğrulamayı ve diğer adlarla DNS Microsoft 365.
ms.custom:
- AdminSurgePortfolio
ms.openlocfilehash: c4282ef4b140fa9e58168ba39c37b4af22b46193
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62987317"
---
# <a name="connect-your-domain-to-microsoft-365"></a>Bağlan'e Microsoft 365

> [!NOTE]
> Etki alanı ekley adresiniz yoksa, siz ekleyene kadar, onmicrosoft.com e-posta adresleri için etki alanınız bu etki alanını kullanır. Kullanıcıları eklemeden önce etki alanınızı eklemeniz önemlidir, böylece onları iki kez ayarlamak zorunda değildir.

[Aşağıda, ne](../setup/domains-faq.yml) arayabilirsiniz?

## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Etki alanınıza gelen e-postanın Microsoft'a göndernsin için MX kaydı ekleme

Yönetim merkezi etki alanı kurulum sihirbazından MX kaydıyla ilgili bilgileri edinebilirsiniz.

Barındırma sağlayıcınızın web sitesinde yeni bir MX kaydı ekleyin.
Alanların aşağıdaki değerlere ayarlanmış olduğundan emin olun:

- Kayıt Türü: `MX`
- Öncelik: Normalde, kullanılabilen en yüksek değere ayarlanır `0`.
- Ana Bilgisayar Adı: `@`
- Points to address: Değeri yönetim merkezinden kopyalayıp buraya yapıştırın.
- TTL: `3600` (veya varsayılan sağlayıcınız)

Kaydı kaydedin ve sonra tüm diğer MX kayıtlarını kaldırın.

## <a name="add-a-cname-record-to-connect-users-to-their-mailboxes"></a>Kullanıcıları posta kutularına bağlamak için CNAME kaydı ekleme

CNAME kayıtlarıyla ilgili bilgileri yönetim merkezi etki alanı kurulum sihirbazından edinebilirsiniz.

Barındırma sağlayıcınızın web sitesine aşağıdaki CNAME kaydını ekleyin. Alanların her biri için aşağıdaki değerlere ayarlanmış olduğundan emin olun:

- Kayıt Türü: `CNAME (Alias)`
- Ana Bilgisayar: Kopyalayıp yönetim merkezinden değerleri buraya yapıştırın.
- Points to address: Değeri yönetim merkezinden kopyalayıp buraya yapıştırın.
- TTL: `3600` (veya varsayılan sağlayıcınız)

## <a name="add-a-txt-record-to-help-prevent-spam"></a>İstenmeyen postayı önlemeye yardımcı olmak için TXT kaydı ekleme

**Başlamadan önce:** Etki alanınız için zaten bir SPF kaydınız varsa, etki alanınız için yeni bir SPF Microsoft 365. Bunun yerine, Microsoft 365 her iki değer kümesi de içeren tek *bir SPF* kaydına sahip olmak için gerekli kayıt değerlerini barındırma sağlayıcıları web sitenize ekleyin.

Barındırma sağlayıcınızın web sitesinde, var olan SPF kaydını düzenleyin veya bir SPF kaydı oluşturun.
Alanların aşağıdaki değerlere ayarlanmış olduğundan emin olun:

- Kayıt Türü: `TXT (Text)`
- Ana Bilgisayar: `@`
- TXT Değeri: `v=spf1 include:spf.protection.outlook.com -all`
- TTL: `3600` (veya varsayılan sağlayıcınız)

Kaydı kaydedin.

Bu SPF doğrulama araçlarından birini kullanarak [SPF kaydınızı doğrulama](/office365/admin/setup/domains-faq#how-can-i-validate-spf-records-for-my-domain)

SPF, ifadeyi önlemeye yardımcı olmak için tasarlanmıştır ancak SPF'nin koruyamaz olduğu sanallık tekniklerini vardır. Bunlara karşı korunmak için, SPF'yi bir kez ayar verdiktan sonra bu alan için DKIM ve DMARC'yi de Microsoft 365.

Kullanmaya başlamak için bkz[. MICROSOFT 365'ta](../../security/office-365-security/use-dkim-to-validate-outbound-email.md) etki alanınıza gönderilen giden e-postayı doğrulamak için DKIM kullanma ve [DMARC](../../security/office-365-security/use-dmarc-to-validate-email.md) kullanarak e-postayı Microsoft 365.

Son olarak, kurulum işlemini tamamlamak için yönetim merkezi etki alanı kurulum sihirbazına geri gidin.
