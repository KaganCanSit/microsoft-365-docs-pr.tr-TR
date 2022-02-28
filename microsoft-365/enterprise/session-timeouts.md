---
title: Oturumlar için oturum zaman Microsoft 365
ms.author: tracyp
author: MSFTTracyP
manager: scotv
ms.date: 6/29/2018
audience: Admin
ms.topic: reference
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 37a5c116-5b07-4f70-8333-5b86fd2c3c40
ms.collection:
- M365-security-compliance
description: Oturum zaman aşımı sürelerinin, istemci uygulamalarıyla ilgili güvenlik ve erişim kolaylığını dengelemek Microsoft 365 öğrenin.
ms.openlocfilehash: f5b7c87cabfd6f80061c2795568cd53955caa10f
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988771"
---
# <a name="session-timeouts-for-microsoft-365"></a>Oturumlar için oturum zaman Microsoft 365

Oturum ömrü, Microsoft 365 kimlik doğrulamasının önemli bir parçasıdır; güvenliği ve kullanıcılara kimlik bilgilerinin sorulma sayısını dengeleme açısından önemli bir bileşendir.

## <a name="session-times-for-microsoft-365-services"></a>Hizmetler için Microsoft 365 süreleri

Kullanıcılar herhangi bir e-posta web Microsoft 365 mobil uygulamalarda kimlik doğrulaması kullandığında, bir oturum kurulur. Oturum süresi boyunca, kullanıcıların yeniden kimlik doğrulamasına gerek olmayacaktır. Kullanıcılar etkin olmayan, tarayıcıyı veya sekmeyi kapatan ya da kimlik doğrulama belirteclerinin süresi sona erdiğinde (parolanın sıfır tarihi gibi diğer nedenlerden dolayı) oturumların süresi dolabiliyor. Hizmet Microsoft 365, her hizmetin kendi kullanım süresine karşılık gelen farklı oturum zaman aşımına sahip olur.

Aşağıdaki tabloda, kullanıcı hizmetleri için oturum yaşam Microsoft 365 listelemektedir:

| Microsoft 365 hizmeti | Oturum zaman aşımı |
|:-----|:-----|
|Microsoft 365 yönetici merkezi  <br/> |Yönetim merkezinin her 8 saatte bir kimlik bilgilerini sağlamanız istenir.  <br/> |
|SharePoint Online  <br/> |Kullanıcılar Oturum açık bırak'ı seçene kadar 5 gün **boyunca etkileşimde değildir**. Kullanıcı önceki oturum açma veya daha fazla saat sonra yeniden SharePoint Online'a erişmişse, zaman aşımı değeri 5 gün olacak şekilde sıfırlanır.  <br/> |
|Outlook Web App  <br/> |6 saat.  <br/> [Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) cmdlet'inde _ActivityBasedAuthenticationTimeoutInterval_ parametresini kullanarak bu değeri değiştirebilirsiniz.  <br/> |
|Azure Active Directory  <br/> (Modern kimlik Office etkinleştirilmiş Microsoft 365 istemcilerde Windows uygulamaları tarafından kullanılır)  <br/> | Modern kimlik doğrulama, kullanıcıya kimlik doğrulama bilgilerini kullanarak kaynak kullanımına erişim Microsoft 365 yenileme belirteçleri ve yenileme Azure Active Directory. Erişim belirteci, başarılı bir kimlik doğrulamasının ardından sağlanan ve 1 saat boyunca geçerli olan bir JSON Web Belirteci'dir. Ayrıca, ömrü daha uzun olan bir yenileme belirteci de sağlanır. Erişim belirteçlerinin süresi dolduğunda, Office yeni bir erişim belirteci almak için geçerli bir yenileme belirteci kullanır. Bu değişim, kullanıcının ilk kimlik doğrulaması hala geçerli ise başarılı olur.  <br/>  Yenileme belirteçleri 90 gün boyunca geçerlidir ve sürekli kullanımla iptal edilene kadar geçerli olabilir.  <br/>  Yenileme belirteçleri, şu gibi çeşitli olaylar tarafından geçersiz kılınıyor olabilir:  <br/>  Yenileme belirteci verilene kadar kullanıcının parolası değişti.  <br/>  Yönetici, kullanıcının erişmeye çalıştığı kaynağa erişimi kısıtlayan koşullu erişim ilkeleri uygulayabilir.  <br/> |
|SharePoint, iOS OneDrive mobil uygulamalarını uygulama ve Windows 10  <br/> |Erişim belirteci için varsayılan yaşam süresi 1 saattir. Yenileme belirtecin varsayılan en uzun etkin olmayan süresi 90 gündür.  <br/> [Belirteçler ve belirteçlerin yaşam sürelerini yapılandırma hakkında daha fazla bilgi](/azure/active-directory/active-directory-configurable-token-lifetimes) <br/> Yenileme belirteci iptal etmek için, kullanıcının yenileme Microsoft 365 sıfırlayabilirsiniz  <br/> |
|Yammer ile Microsoft 365 Sign-In  <br/> |Tarayıcının ömrüne göre. Kullanıcılar tarayıcıyı kapatır ve yeni Yammer tarayıcıdan erişim sağlarsa, Yammer kimlik doğrulama bilgileriyle yeniden Microsoft 365. Kullanıcılar, tanımlama bilgilerini önbelleğe alan üçüncü taraf tarayıcılar kullanıyorsa, tarayıcıyı yeniden açtıklarda yeniden kimlik doğrulaması yapmaları gerekmeyebilirsiniz.  <br/> > [!NOTE]> Bu yalnızca E-posta için Microsoft 365 Sign-In kullanan Yammer.           |