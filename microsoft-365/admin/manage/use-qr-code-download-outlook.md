---
title: QR kodunu kullanarak mobil uygulamalarda oturum Outlook kullanma
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
description: QR kodunu mobil cihazlarda kimlik doğrulaması yapmak ve indirmek için Outlook öğrenin.
ms.openlocfilehash: 736628fb97cf2a6f4f6c6d175384a30c41bf642d
ms.sourcegitcommit: 7f0c5b55e2966c0c1ce6a153a4e6a7ec035bd818
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2021
ms.locfileid: "63007651"
---
# <a name="use-a-qr-code-to-sign-in-to-the-outlook-mobile-apps"></a>QR kodunu kullanarak mobil uygulamalarda oturum Outlook kullanma

Sistem Microsoft 365 olarak kullanıcılarınızı, kullanıcı adı ve parolalarını girmek zorunda kalmadan mobil cihazlarında Android veya iOS için Outlook'de oturum açmalarını sebilirsiniz. QR kodunu tarayarak, kullanıcılar güvenli bir şekilde kimlik doğrulaması ve mobil cihazlarda oturum Outlook kullanabilir.

Masaüstü Web üzerinde Outlook diğer masaüstü Outlook uygulamalarında, kullanıcılar mobil cihazlarında Outlook kullanabileceği konusunda bilgien bildirimler görebilirler. Bu bildirimler, yönetici tarafından Exchange PowerShell kullanılarak yönetilebilir. Kullanıcılar uygulamayı mobil cihazlarında indirmek için kendilerine SMS mesajı göndermeyi seçerse, bilgisayarlarında bir QR kodu görünür. QR kodunu tarayarak telefon veya tabletlerinden Outlook oturum açabilecektir. Bu QR kodu, yalnızca bir kez 1 kez ed binen kısa, yaşanmış bir belirteçtir.

Bildirim yalnızca aşağıdaki koşullar karşılandı ise oluşturulur:

1. Kiracı için QR kodu deneyimi etkinleştirilir (bu deneyim varsayılan olarak etkindir).

2. Kullanıcı zaten iOS ve Android için Outlook'i kullanmamış olabilir.

3. Kullanıcının okuma bölmesinde boş bir durumu vardır (ilk e-postayı otomatik açma seçeneği seçili değildir).

4. Kullanıcı bildirimi reddetti.

> [!NOTE]
> Bazı durumlarda, kullanıcılarının QR kodunu oluşturmak için bilgisayarlarında yeniden kimlik doğrulaması yapmaları gerekir.

## <a name="use-exchange-powershell"></a>Exchange PowerShell kullanma

Bu özellik varsayılan olarak açıktır. Bu özelliği devre dışı bırakmak için aşağıdaki adımları izleyin.

1. [Bağlan PowerShell Exchange e geri tarak.](/powershell/exchange/connect-to-exchange-online-powershell)
2. PowerShell'i kullanarak kullanıcılarınıza mobil uygulamalar hakkında bildirim Outlook devre dışı abilirsiniz. Bu, QR kodu oturum açma akışının  gösteriliyor olması da önler.

```powershell
Set-OrganizationConfig -MobileAppEducationEnabled <Boolean>
```

> [!NOTE]
> Exchange PowerShell komutu kullanırken, değişikliklerin yayılması 8 saat kadar sürebilir.

## <a name="related-content"></a>İlgili içerik

[Standart veya Hedefli sürüm seçeneklerini ayarlama](release-options-in-office-365.md) (makale)\
[Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) (makale)
