---
title: Paylaşılan posta kutularından karantinaya alınan iletileri görüntüleme ve bırakma
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: ''
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
ROBOTS: NOINDEX
description: Kullanıcılar, izinlerine sahip oldukları paylaşılan posta kutularına gönderilen karantinaya alınmış iletileri görüntülemeyi ve üzerinde işlem yapmayı öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2613d3b8be200db3a9107355a27b0dd79ce537d3
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647342"
---
# <a name="view-and-release-quarantined-messages-from-shared-mailboxes"></a>Paylaşılan posta kutularından karantinaya alınan iletileri görüntüleme ve bırakma

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Şunlar için geçerlidir:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Kullanıcılar karantinaya alınan iletileri, [EOP'de kullanıcı olarak karantinaya alınan iletileri bulma ve bırakma](find-and-release-quarantined-messages-as-a-user.md) başlığında açıklandığı gibi alıcılardan biri oldukları durumlarda yönetebilir. Peki kullanıcının Exchange Online **paylaşılan posta kutuları** bölümünde açıklandığı gibi posta kutusuna Tam Erişim ve Farklı Gönder veya Adına Gönder izinlerine sahip olduğu [paylaşılan posta kutularına](/exchange/collaboration-exo/shared-mailboxes) ne olacak?

Daha önce, kullanıcıların paylaşılan posta kutusuna gönderilen karantinaya alınmış iletileri yönetebilmesi için yöneticilerin paylaşılan posta kutusu için otomatik eşlemeyi etkin bırakması gerekiyordu (yönetici kullanıcıya başka bir posta kutusuna erişim verdiğinde varsayılan olarak etkindir). Ancak, kullanıcının erişimi olan posta kutularının boyutuna ve sayısına bağlı olarak, Outlook'lar kullanıcının erişimi olan _tüm_ posta kutularını açmaya çalıştığında performans olumsuz olabilir. Bu nedenle, birçok yönetici [paylaşılan posta kutuları için otomatik eşlemeyi kaldırmayı](/outlook/troubleshoot/profiles-and-accounts/remove-automapping-for-shared-mailbox) seçer.

Artık kullanıcıların paylaşılan posta kutularına gönderilen karantinaya alınan iletileri yönetmesi için otomatik eşleme gerekli değildir. Sadece işe yarıyor. Paylaşılan posta kutusuna gönderilen karantinaya alınmış iletilere erişmek için iki farklı yöntem vardır:

- Yönetici karantina bildirimlerine (eski adıyla son kullanıcı istenmeyen posta bildirimleri) izin vermek için [karantina ilkelerini](quarantine-policies.md) yapılandırdıysa, paylaşılan posta kutusunda karantina bildirimlerine erişimi olan tüm kullanıcılar Microsoft 365 Defender portalında karantinaya gitmek için bildirimdeki **Gözden Geçir** düğmesine tıklayabilir. Bu yöntemin kullanıcıların yalnızca paylaşılan posta kutusuna gönderilen karantinaya alınmış iletileri yönetmesine izin verdiğine dikkat edin. Kullanıcılar bu bağlamda kendi karantina iletilerini yönetemez.
- Kullanıcı [Microsoft 365 Defender portalında karantinaya alabilir](find-and-release-quarantined-messages-as-a-user.md) ve sonuçları **Alıcı adresine** (paylaşılan posta kutusunun e-posta adresi) göre filtrelemek için **Filtre'ye** tıklayabilir. Ana **Karantina** sayfasında, paylaşılan posta kutusuna gönderilen iletilere göre sıralamak için **Alıcı** sütununa tıklayabilirsiniz.

## <a name="things-to-keep-in-mind"></a>Akılda tutulması gerekenler

- _Karantina ilkeleri_ , kullanıcıların karantinaya alınan iletilere ne yapmalarına veya yapmalarına izin verilip verilmeyeceğini, iletinin neden karantinaya alındığına (desteklenen özellikler için) göre tanımlar. Varsayılan karantina ilkeleri, alıcıların iletileri görüntülemesine ve üzerinde işlem yapmalarına olanak sağlayan geçmiş özellikleri zorunlu kıldığını gösterir. Yöneticiler, kullanıcılar için daha az kısıtlayıcı veya daha kısıtlayıcı özellikler tanımlayan özel karantina ilkeleri oluşturabilir ve uygulayabilir. Daha fazla bilgi için bkz [. Karantina ilkeleri](quarantine-policies.md).

- Karantinaya alınan ileti üzerinde işlem yapan ilk kullanıcı, paylaşılan posta kutusunu kullanan herkes için iletinin kaderine karar verir. Örneğin, paylaşılan posta kutusuna 10 kullanıcı erişirse ve bir kullanıcı karantina iletisini silmeye karar verirse, ileti 10 kullanıcının tümü için silinir. Benzer şekilde, kullanıcı iletiyi yayınlamaya karar verirse, paylaşılan posta kutusuna gönderilir ve paylaşılan posta kutusunun diğer tüm kullanıcıları tarafından erişilebilir.

- Şu anda Paylaşılan posta kutusuna gönderilen karantinaya alınan iletiler için **Ayrıntılar** açılır penceresinde **Göndereni engelle** düğmesi kullanılamaz.

- Paylaşılan posta kutuları için karantina işlemleriyle ilgili olarak, paylaşılan bir posta kutusuna erişim vermek için iç içe güvenlik grupları kullanıyorsanız, iki düzeyden fazla iç içe grup kullanmanızı öneririz. Örneğin, Grup A, C Grubunun üyesi olan B Grubunun bir üyesidir. Paylaşılan posta kutusuna izin atamak için kullanıcıyı A Grubu'na eklemeyin ve ardından paylaşılan posta kutusuna C Grubu atayın.  

- [Exchange Online PowerShell'de](/powershell/exchange/connect-to-exchange-online-powershell) paylaşılan posta kutusu için karantinaya alınan iletileri yönetmek için, son kullanıcının iletileri tanımlamak üzere _RecipientAddress_ parametresinin değeri için paylaşılan posta kutusu [e-posta adresiyle Get-QuarantineMessage](/powershell/module/exchange/get-quarantinemessage) cmdlet'ini kullanması gerekir. Örneğin:

  ```powershell
  Get-QuarantineMessage -RecipientAddress officeparty@contoso.com
  ```

  Ardından, son kullanıcı görüntülemek veya üzerinde işlem yapmak için listeden karantinaya alınmış bir ileti seçebilir.

  Bu örnek, paylaşılan posta kutusuna gönderilen karantinaya alınmış tüm iletileri gösterir ve ardından listedeki ilk iletiyi karantinadan serbest bırakır (listedeki ilk ileti 0, ikinci ileti 1 vb.).

  ```powershell
  $SharedMessages = Get-QuarantineMessage -RecipientAddress officeparty@contoso.com | select -ExpandProperty Identity
  $SharedMessages
  Release-QuarantineMessage -Identity $SharedMessages[0]
  ```

  Ayrıntılı söz dizimi ve parametre bilgileri için aşağıdaki konulara bakın:

  - [Get-QuarantineMessage](/powershell/module/exchange/get-quarantinemessage)
  - [Get-QuarantineMessageHeader](/powershell/module/exchange/get-quarantinemessageheader)
  - [Preview-QuarantineMessage](/powershell/module/exchange/preview-quarantinemessage)
  - [Release-QuarantineMessage](/powershell/module/exchange/release-quarantinemessage)
