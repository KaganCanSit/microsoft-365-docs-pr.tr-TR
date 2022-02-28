---
title: Paylaşılan posta kutularından karantinaya alınan iletileri görüntüleme ve serbest bırakma
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
description: Kullanıcılar, izinleri olan paylaşılan posta kutularına gönderilen karantinaya alınmış iletileri görüntülemeyi ve bu iletiler üzerinde eylem yapmayı öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e78a46bca97ea58a88195c9d05e11332528cf3af
ms.sourcegitcommit: 317fab13e84b2867087a6ba0a593313ecf43bbed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2021
ms.locfileid: "62988815"
---
# <a name="view-and-release-quarantined-messages-from-shared-mailboxes"></a>Paylaşılan posta kutularından karantinaya alınan iletileri görüntüleme ve serbest bırakma

> [!NOTE]
> Bu makalede açıklanan özellikler şu anda Önizleme'dedir, herkes tarafından kullanılamaz ve değişebilir.

Kullanıcılar, [EOP'de](find-and-release-quarantined-messages-as-a-user.md) kullanıcı olarak karantinaya alınmış iletileri bulma ve bırakma konusunda açıklandığı gibi, alıcılardan biri olduğu karantinaya alınmış iletileri yönetebilir. Peki **, kullanıcının Tam** Erişim ve Farklı Gönder veya Adına Gönder izinlerine sahip olduğu paylaşılan posta kutularında, kullanıcı e-posta kutusunda paylaşılan [posta](/exchange/collaboration-exo/shared-mailboxes) kutularında Exchange Online?

Daha önce, kullanıcıların paylaşılan posta kutusuna gönderilen karantinaya alınmış iletileri yönetebilme özelliği, yöneticilerin paylaşılan posta kutusunda otomatik kırpmayı etkin bırakabilmeleri gerekir (yönetici kullanıcı başka bir posta kutusuna erişim izni verdiği zaman varsayılan olarak etkindir). Bununla birlikte, kullanıcının erişim izni olan posta kutularının boyutuna ve sayısına bağlı olarak, Outlook kullanıcının erişim izni olan tüm posta kutularını açmaya çalıştığında  performansta bir performans az olabilir. Bu nedenle, birçok yönetici paylaşılan posta [kutuları için otomatik kırpmayı kaldırmayı seçer](/outlook/troubleshoot/profiles-and-accounts/remove-automapping-for-shared-mailbox).

Artık kullanıcıların paylaşılan posta kutularına gönderilen karantinaya alınmış iletileri yönetmesi için otomatik kırpma gerekmiyor. Yalnızca işe yarar. Paylaşılan posta kutusuna gönderilmiş olan karantinaya alınmış iletilere erişmek için iki farklı yöntem vardır:

- Yönetici karantina bildirimlerine (eski [](quarantine-policies.md) adıyla son kullanıcı istenmeyen posta bildirimleri) izin verecek şekilde karantina ilkelerini yapılandırmışsa, paylaşılan posta kutusunda karantina bildirimlerine erişimi olan tüm kullanıcılar, Microsoft 365 Defender portalında karantinaya gitmek için bildirimde  Gözden Geçir düğmesine tıklar. Bu yöntemin yalnızca kullanıcıların paylaşılan posta kutusuna gönderilen karantinaya alınmış iletileri yönetmeye izin verir. Kullanıcılar bu bağlamda kendi karantina iletilerini yönete değildir.
- Kullanıcı, alıcı [portalında karantinaya Microsoft 365 Defender ve](find-and-release-quarantined-messages-as-a-user.md) sonuçları Alıcı  adresine **(paylaşılan** posta kutusunun e-posta adresi) göre filtrelemek için Filtre'ye tıklayın. Ana Karantina **sayfasında** Alıcı sütununu **tıklatın ve paylaşılan** posta kutusuna gönderilmiş iletilere göre sıralayın.

## <a name="things-to-keep-in-mind"></a>Gözlerde tutma gerekenler

- _Karantina ilkeleri_ , iletinin neden karantinaya alındığına (desteklenen özellikler için) bağlı olarak, kullanıcıların karantinaya alınmış iletilerde neler yapmalarına izin verilmiyor veya verilmeyecekleri tanımlar. Varsayılan karantina ilkeleri, alıcıların iletileri görüntülemesine ve üzerinde eylemde olmasına olanak sağlayan geçmiş özelliklerini zorunlu kullanır. Yöneticiler, kullanıcılar için daha az kısıtlayıcı veya daha kısıtlayıcı özellikler tanımlayan özel karantina ilkeleri oluşturabilir ve uygulayabilir. Daha fazla bilgi için bkz. [Karantina ilkeleri](quarantine-policies.md).

- Karantinaya alınan ileti üzerinde ilk kullanıcı, paylaşılan posta kutusunu kullanan herkes için iletinin ne olduğuna karar verir. Örneğin, paylaşılan posta kutusuna 10 kullanıcı erişmişse ve kullanıcı karantina iletisine karar veriyorsa, ileti 10 kullanıcının hepsi için silinir. Benzer şekilde, kullanıcı iletiyi serbest bırakma kararı alırsa, paylaşılan posta kutusunda serbesttir ve paylaşılan posta kutusunun diğer tüm kullanıcıları tarafından erişilebilir.

- Şu anda, **paylaşılan posta** kutusuna gönderilen karantinaya **alınmış** iletiler için Göndereni engelle düğmesi Ayrıntılar uç kutusunda kullanılamaz.

- Paylaşılan posta kutuları için karantina işlemleriyle ilgili olarak, paylaşılan bir posta kutusuna erişim vermek üzere iç içe güvenlik gruplarını kullanırsanız, iç içe grupların iki düzeyden fazlasını önerilmez. Örneğin, A Grubu B Grubunun bir üyesidir ve C Grubunun üyesidir. Paylaşılan posta kutusuna izinler atamak için, kullanıcıları A Grubu'nda eklemein ve ardından C Grubu'nda paylaşılan posta kutusuna atamayın.  

- [Exchange Online PowerShell'de](/powershell/exchange/connect-to-exchange-online-powershell) paylaşılan posta kutusu için karantinaya alınmış iletileri yönetmek için, son kullanıcının iletileri tanımlamak üzere _RecipientAddress_ parametresi değerinin paylaşılan posta kutusu [e-posta adresiyle Get-QuarantineMessage](/powershell/module/exchange/get-quarantinemessage) cmdlet'ini kullanması gerekir. Örneğin:

  ```powershell
  Get-QuarantinedMessage -RecipientAddress officeparty@contoso.com
  ```

  Daha sonra, son kullanıcı görüntülemek veya üzerinde işlem yapmak için listeden karantinaya alınmış iletiyi seçer.

  Bu örnekte, paylaşılan posta kutusuna gönderilmiş olan karantinaya alınmış tüm iletiler görüntülenir ve sonra da listenin ilk iletisi karantinadan çıkarılır (listenin ilk iletisi 0, ikinci ileti 1 olur, vb.).

  ```powershell
  $SharedMessages = Get-QuarantinedMessage -RecipientAddress officeparty@contoso.com | select -ExpandProperty Identity
  $SharedMessages
  Release-QuarantinedMessage -Identity $SharedMessages[0]
  ```

  Ayrıntılı söz dizimi ve parametre bilgileri için aşağıdaki konulara bakın:

  - [Get-QuarantineMessage](/powershell/module/exchange/get-quarantinemessage)
  - [Get-QuarantineMessageHeader](/powershell/module/exchange/get-quarantinemessageheader)
  - [Preview-QuarantineMessage](/powershell/module/exchange/preview-quarantinemessage)
  - [Release-QuarantineMessage](/powershell/module/exchange/release-quarantinemessage)
