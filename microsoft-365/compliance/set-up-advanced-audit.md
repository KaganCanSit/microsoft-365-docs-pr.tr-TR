---
title: Gelişmiş Denetim'i Microsoft 365
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
description: Bu makalede, kullanıcı hesaplarının güvenliği ihlal edilmişken veya güvenlikle ilgili diğer olayları araştırmanız için araştırma araştırma gerçekleştirmek üzere Gelişmiş Denetim'in nasıl ayarıldığı açıklanmıştır.
ms.openlocfilehash: dafe53161e04f28f2f5e4ff8dcfa71bab6c1a1f1
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754571"
---
# <a name="set-up-advanced-audit-in-microsoft-365"></a>Gelişmiş Denetim'i Microsoft 365

Kuruluşta Gelişmiş Denetimi destekleyen bir abonelik ve son kullanıcı lisansı varsa, Gelişmiş Denetim'de ek özellikleri ayarlamak ve kullanmak için aşağıdaki adımları uygulayın.

![Gelişmiş Denetimi ayarlamak için iş akışı.](../media/AdvancedAuditWorkflow.png)

## <a name="step-1-set-up-advanced-audit-for-users"></a>1. Adım: Kullanıcılar için Gelişmiş Denetimi ayarlama

MailItemsAccessed ve Send gibi önemli olayları günlüğe yazma yeteneği gibi gelişmiş Denetim özellikleri, kullanıcılara uygun bir E5 lisansı atamayı gerektirir. Buna ek olarak, bu kullanıcılar için Gelişmiş Denetim uygulaması/hizmet planı da etkinleştirilmelidir. Gelişmiş Denetim uygulamasının kullanıcılara atanıyor olduğunu doğrulamak için, her kullanıcı için aşağıdaki adımları uygulayın:

1. Etkin Microsoft 365 yönetim merkezi **Kullanıcılar'a** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**gidin ve**</a> bir kullanıcı seçin.

2. Kullanıcı özellikleri uç sayfasında Lisanslar ve **uygulamalar'a tıklayın**.

3. Lisanslar **bölümünde** , kullanıcıya E5 lisansı atanarak veya uygun bir eklenti lisansı atanarak atan olduğunu doğrulayın. Gelişmiş Denetimi destekleyen lisansların listesi için bkz. [Gelişmiş Denetim lisans gereksinimleri](auditing-solutions-overview.md#advanced-audit-1).

4. Uygulamalar **bölümünü** genişletin ve Gelişmiş Denetim onay **Microsoft 365 kutusunun seçili** olduğunu doğrulayın.

5. Onay kutusu seçili değilse, onay kutusunu seçin ve ardından Değişiklikleri **kaydet'e tıklayın.**

   MailItemsAccessed ve Send için denetim kayıtlarının günlüğü 24 saat içinde başlar. Diğer iki Gelişmiş Denetim olayını günlüğe kaydetmeye başlamak için 3. Adımı gerçekleştirmeniz gerek: SearchQueryInitiatedExchange ve SearchQueryInitiatedSharePoint.

Ayrıca, kullanıcı posta kutularından veya paylaşılan posta kutularından oturum açan posta kutusu eylemlerini özelleştirmiş durumdaysanız, Microsoft tarafından yayımlanan tüm yeni Gelişmiş Denetim olayları bu posta kutularından otomatik olarak denetlenz. Her oturum açma türü için denetlenen posta kutusu eylemlerini değiştirme hakkında bilgi için Posta kutusu denetimini yönetme'nin "Varsayılan olarak günlüğe kaydedilen posta kutusu eylemlerini değiştirme veya geri yükleme" [bölümüne bakın](enable-mailbox-auditing.md#change-or-restore-mailbox-actions-logged-by-default).

## <a name="step-2-enable-advanced-audit-events"></a>2. Adım: Gelişmiş Denetim olaylarını etkinleştirme

Kullanıcılar Exchange Online SharePoint Online'da arama gerçekleştirebilirken, iki Gelişmiş Denetim olaylar (SearchQueryInitiatedExchange ve SearchQueryInitiatedSharePoint) günlüğe SharePoint gerekir. Bu iki olay kullanıcılar için denetlenebilir olarak etkinleştirmek için, powershell'de aşağıdaki komutu (her kullanıcı [için) Exchange Online çalıştırın](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Set-Mailbox <user> -AuditOwner @{Add="SearchQueryInitiated"}
```

Çok coğrafi bir ortamda, kullanıcının posta kutusunun bulunduğu ormanın **önceki Set-Mailbox** komutunu çalıştırmanız gerekir. Kullanıcının posta kutusu konumunu tanımlamak için aşağıdaki komutu çalıştırın: 

```powershell
Get-Mailbox <user identity> | FL MailboxLocations
```

Arama sorguları denetimini etkinleştirme komutu daha önce kullanıcının posta kutusundan farklı bir orman içinde çalıştırıldısa, çalıştırarak kullanıcının posta kutusundan SearchQueryInitiated `Set-Mailbox -AuditOwner @{Remove="SearchQueryInitiated"}` değerini kaldırmanız ve sonra da bu değeri kullanıcının posta kutusunun bulunduğu orman içinde kullanıcının posta kutusuna eklemeniz gerekir.

## <a name="step-3-set-up-audit-retention-policies"></a>3. Adım: Denetim bekletme ilkelerini ayarlama

Exchange, SharePoint ve Azure AD denetim kayıtlarını bir yıl süreyle alıkoyan varsayılan ilkeye ek olarak, kuruluşun güvenlik işlemleri, IT ve uyumluluk ekiplerinin gereksinimlerini karşılamak için ek denetim günlüğü bekletme ilkeleri oluşturabilirsiniz. Daha fazla bilgi için bkz [. Denetim günlüğü bekletme ilkelerini yönetme](audit-log-retention-policies.md).

## <a name="step-4-search-for-advanced-audit-events"></a>4. Adım: Gelişmiş Denetim olaylarını arama

Artık organizasyon için Gelişmiş Denetim'i ayara sahip olduğunuz için araştırma araştırmalarında çok önemli Gelişmiş Denetim olayları ve diğer etkinlikleri arayabilirsiniz. 1. Adım ve 2. Adımı tamamladıktan sonra, güvenliği tehlikeye atılmış hesaplarda ve diğer türlerde güvenlik ve uyumluluk soruşturmaları ile ilgili araştırmalarda Gelişmiş Denetim olayları ve diğer etkinlikler için denetim günlüğünde arama gerçekleştirebilirsiniz. MailItemsAccessed Advanced Audit olayı kullanarak güvenliği ihlal edilmiş kullanıcı hesapları hakkında araştırma yapmak hakkında daha fazla bilgi için, Güvenliği ihlal edilmiş hesapları araştırmak için Gelişmiş [Denetim'i kullanma'ya bakın](mailitemsaccessed-forensics-investigations.md).
