---
title: IPv6 üzerinden anonim gelen e-posta için destek ekleme
f1.keywords:
- NOCSH
author: chrisda
ms.author: chrisda
manager: chrisda
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: b68df621-0a5f-4824-8abc-41e0c4fd1398
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Yönetici, genel grup ve adres mektuplarında IPv6 kaynaklarından anonim gelen e-Exchange Online Exchange Online Protection.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 78b2e653aa284e34af2315ac696d7390dce71884
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2021
ms.locfileid: "63008899"
---
# <a name="add-support-for-anonymous-inbound-email-over-ipv6-in-microsoft-365"></a>Adres mektuplarında IPv6 üzerinden anonim gelen e-posta için Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft 365 posta kutuları Exchange Online bağımsız Exchange Online Protection (EOP) kuruluşları Exchange Online kuruluşlar, IPv6 üzerinden anonim gelen e-postayı destekler. Kaynak IPv6 e-posta sunucusu aşağıdaki gereksinimlerin ikisini de karşılamalıdır:

- Kaynak IPv6 adresi, hedefin IPv6 adresindeki etki alanı adını bulmasını sağlayan geçerli bir ters DNS araması (PTR) kaydına sahip olmalıdır.

- Gönderen SPF doğrulamayı ( [RFC 7208'de](https://tools.ietf.org/html/rfc7208) tanımlanmış) veya [DKIM](http://dkim.org/) doğrulamayı ( [RFC 6376'da tanımlanmış) geçmek gerekir](https://www.rfc-editor.org/rfc/rfc6376.txt).

Kuruluşun IPv6 üzerinden anonim gelen e-posta al önce, bir yöneticinin Microsoft desteğine başvurarak bunu istemesi gerekir. Destek isteği açma yönergeleri için bkz. İş ürünleri için [de yardıma başvurun - Yönetici Yardımı](../../admin/get-help-support.md).

Anonim gelen IPv6 ileti desteği kuruluşta etkinleştirildikten sonra, ileti hizmet tarafından sağlanan normal ileti filtrelemesinden geçmektedir.

## <a name="troubleshooting"></a>Sorun giderme

- Kaynak e-posta sunucusunda IPv6 ters DNS arama kaydı yoksa, iletiler aşağıdaki hatayla reddedilir:

  > 450 4.7.25 Hizmet kullanılamıyor, IPv6 adresi gönderilemiyor [2a01:111:f200:2004::240], TERS DNS kaydına sahip olmalı.

- Gönderen SPF veya DKIM doğrulamasını geçezse, iletiler aşağıdaki hatayla reddedilir:

  > 450 4.7.26 Hizmet kullanılamıyor, IPv6 üzerinden gönderilen ileti [2a01:111:f200:2004::240], SPF veya DKIM doğrulamasını geçsin.

- Anonim IPv6 iletilerini kabul edene kadar almayı denersanız, ileti aşağıdaki hatayla reddedilir:

  > 550 5.2.1 Hizmet kullanılamıyor, [contoso.com] IPv6 üzerinden e-posta kabul etmiyor.

## <a name="related-topics"></a>İlgili konular

[DKIM imzalı iletileri doğrulama desteği](support-for-validation-of-dkim-signed-messages.md)
