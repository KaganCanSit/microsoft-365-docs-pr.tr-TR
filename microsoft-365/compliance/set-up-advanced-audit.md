---
title: Microsoft 365'de Denetimi (Premium) ayarlama
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-audit
- m365initiative-compliance
- m365solution-scenario
ms.custom: admindeeplinkMAC
search.appverid:
- MOE150
- MET150
description: Bu makalede, kullanıcı hesapları tehlikeye atıldığında veya güvenlikle ilgili diğer olayları araştırmak için adli incelemeler yapabilmeniz için Denetimin (Premium) nasıl ayarlanacağı açıklanır.
ms.openlocfilehash: 9e758ce6a830569b007ee024e17abdddbce01f13
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64945857"
---
# <a name="set-up-microsoft-purview-audit-premium"></a>Microsoft Purview Denetimini Ayarlama (Premium)

Kuruluşunuzun Denetimi (Premium) destekleyen bir aboneliği ve son kullanıcı lisansı varsa, Denetim (Premium) bölümündeki ek özellikleri ayarlamak ve kullanmak için aşağıdaki adımları gerçekleştirin.

![Denetimi ayarlamak için iş akışı (Premium).](../media/AdvancedAuditWorkflow.png)

## <a name="step-1-set-up-audit-premium-for-users"></a>1. Adım: Kullanıcılar için Denetim (Premium) ayarlama

MailItemsAccessed ve Send gibi önemli olayları günlüğe kaydetme özelliği gibi denetim (Premium) özellikleri için kullanıcılara uygun bir E5 lisansı atanması gerekir. Ayrıca, bu kullanıcılar için Gelişmiş Denetim uygulaması/hizmet planı etkinleştirilmelidir. Gelişmiş Denetim uygulamasının kullanıcılara atandığını doğrulamak için her kullanıcı için aşağıdaki adımları uygulayın:

1. Microsoft 365 yönetim merkezi <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**KullanıcılarEtkin**</a> >  kullanıcılar'a gidin ve bir kullanıcı seçin.

2. Kullanıcı özellikleri açılır sayfasında **Lisanslar ve uygulamalar'a** tıklayın.

3. **Lisanslar** bölümünde, kullanıcıya bir E5 lisansı atandığını veya uygun bir eklenti lisansı atandığını doğrulayın. Denetim (Premium) destekleyen lisansların listesi için bkz. [Denetim (Premium) lisans gereksinimleri](auditing-solutions-overview.md#audit-premium-1).

4. **Uygulamalar** bölümünü genişletin ve **gelişmiş denetim Microsoft 365** onay kutusunun seçili olduğunu doğrulayın.

5. Onay kutusu seçili değilse, onay kutusunu seçin ve ardından **Değişiklikleri kaydet'e tıklayın.**

   MailItemsAccessed ve Send denetim kayıtlarının günlüğe kaydedilmesi 24 saat içinde başlar. Diğer iki Audit (Premium) olayını günlüğe kaydetmeye başlamak için 3. Adımı gerçekleştirmeniz gerekir: SearchQueryInitiatedExchange ve SearchQueryInitiatedSharePoint.

Ayrıca, kullanıcı posta kutularında veya paylaşılan posta kutularında oturum açan posta kutusu eylemlerini özelleştirdiyseniz, Microsoft tarafından yayımlanan yeni Denetim (Premium) olayları bu posta kutularında otomatik olarak denetlenmeyecek. Her oturum açma türü için denetlenen posta kutusu eylemlerini değiştirme hakkında bilgi için, Posta kutusu [denetimini yönetme](enable-mailbox-auditing.md#change-or-restore-mailbox-actions-logged-by-default) bölümündeki "Varsayılan olarak günlüğe kaydedilen posta kutusu eylemlerini değiştirme veya geri yükleme" bölümüne bakın.

## <a name="step-2-enable-audit-premium-events"></a>2. Adım: Denetim (Premium) olaylarını etkinleştirme

Kullanıcılar Exchange Online ve SharePoint Online'da arama yaparken iki Audit (Premium) olayının (SearchQueryInitiatedExchange ve SearchQueryInitiatedSharePoint) günlüğe kaydedilmesini etkinleştirmeniz gerekir. Bu iki olayın kullanıcılar için denetlenebilmesini sağlamak için [PowerShell'Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell) aşağıdaki komutu (her kullanıcı için) çalıştırın:

```powershell
Set-Mailbox <user> -AuditOwner @{Add="SearchQueryInitiated"}
```

Çok coğrafi bir ortamda, kullanıcının posta kutusunun bulunduğu ormanda önceki **Set-Mailbox** komutunu çalıştırmanız gerekir. Kullanıcının posta kutusu konumunu belirlemek için aşağıdaki komutu çalıştırın: 

```powershell
Get-Mailbox <user identity> | FL MailboxLocations
```

Arama sorgularının denetimini etkinleştirme komutu daha önce kullanıcının posta kutusunun bulunduğundan farklı bir ormanda çalıştırıldıysa, komutunu çalıştırarak `Set-Mailbox -AuditOwner @{Remove="SearchQueryInitiated"}` kullanıcının posta kutusundan SearchQueryInitiated değerini kaldırmanız ve ardından kullanıcının posta kutusunun bulunduğu ormandaki kullanıcının posta kutusuna eklemeniz gerekir.

## <a name="step-3-set-up-audit-retention-policies"></a>3. Adım: Denetim saklama ilkelerini ayarlama

Exchange, SharePoint ve Azure AD denetim kayıtlarını bir yıl boyunca saklayan varsayılan ilkeye ek olarak, kuruluşunuzun güvenlik operasyonları, BT ve uyumluluk ekiplerinin gereksinimlerini karşılamak için ek denetim günlüğü saklama ilkeleri oluşturabilirsiniz. Daha fazla bilgi için bkz. [Denetim günlüğü saklama ilkelerini yönetme](audit-log-retention-policies.md).

## <a name="step-4-search-for-audit-premium-events"></a>4. Adım: Denetim (Premium) olaylarını arama

Kuruluşunuz için Denetim (Premium) ayarladığınıza göre, adli araştırma yaparken kritik Denetim (Premium) olayları ve diğer etkinlikleri arayabilirsiniz. 1. Adım ve 2. Adım'ı tamamladıktan sonra, güvenliği aşılmış hesapların ve diğer güvenlik veya uyumluluk araştırmalarının adli araştırmaları sırasında denetim günlüğünde Denetim (Premium) olayları ve diğer etkinlikler için arama yapabilirsiniz. MailItemsAccessed Audit (Premium) olayını kullanarak güvenliği aşılmış kullanıcı hesaplarıyla ilgili adli inceleme yürütme hakkında daha fazla bilgi için bkz. [Güvenliği aşılmış hesapları araştırmak için Denetimi (Premium) Kullanma](mailitemsaccessed-forensics-investigations.md).
