---
title: Multi-Geo Capabilities in Microsoft Teams
ms.reviewer: daro
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
- m365solution-scenario
- m365solution-spintranet
ms.localizationpriority: medium
description: Multi-Geo Teams çalışma Microsoft 365 nasıl çalıştığını öğrenin.
ms.openlocfilehash: 0315a9ff0429c5e00c662bd7345a3b6a39a591c3
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019453"
---
# <a name="multi-geo-capabilities-in-microsoft-teams"></a>Multi-Geo özellikleri Microsoft Teams

Multi-Geo özellikleri Teams sohbet Teams belirli bir coğrafi konumda saklanabilir. Sohbet verileri özel iletiler, kanal iletileri ve sohbetlerde kullanılan resimler dahil olmak üzere sohbet iletilerinden oluşur.

Teams verilerin nerede depola ilgili olduğunu belirlemek üzere kullanıcılar ve gruplar için Tercih Edilen Veri Konumu(PDL) kullanılır. PDL ayarlanamıyorsa veya geçersizse veriler kiracının merkezi konumda depolanır.

> [!NOTE]
> Multi-Geo özellikleri Teams Temmuz 2021'de tümeyle açıklanacak. Sohbet ve kanal iletileriniz önümüzdeki birkaç çeyrek içinde otomatik olarak doğru coğrafi konuma geçirilir. Kiracı ilk eşitlemeyi tamamlandıktan sonra tüm yeni PDL değişiklikleri işlenir ve bundan sonra yeni PDL değişiklikleri alınıldıktan ve alındıktan sonra işlenecektir.

## <a name="user-chat"></a>Kullanıcı sohbeti

Kullanıcı sohbeti bire bir, bire çok ve özel toplantı iletileri içerir.

Yeni bir kullanıcı oluşturulduğunda, Teams PDL'sini okur ve tüm sohbet verilerini bu coğrafi konumda depolar.

Var olan kullanıcılar için, yönetici kullanıcının PDL'sini ekler veya değiştirebilirse, bu kullanıcının sohbet verileri belirtilen coğrafi konuma taşınarak geçiş sırasına eklenir.

Bire bir veya bire çok sohbetin depolama konumu, sohbeti oluşturan kişinin PDL'sinde temel oluşturulur. Bu kullanıcının PDL'si değiştirilirse, sohbet yeni coğrafi konuma geçirilir. Toplantı sohbeti depolama konumu, toplantı düzenleyicisinin PDL'sinde temel esasdır.

Kullanıcının en son verilerini geçerli konumunu bulmak Teams, [Teams PowerShell'e](/powershell/module/teams/connect-microsoftteams) bağlanın ve aşağıdaki komutu çalıştırın:

```PowerShell
Get-MultiGeoRegion -EntityType User -EntityId <UPN>
```

## <a name="channel-messages"></a>Kanal iletileri

Her Microsoft 365, ilgili verilerin depolandığı coğrafi konumun notlandığı Tercih Edilen Veri Konumu'nda (PDL) yer almaktadır. Teams, her ekiple ilişkilendirilmiş grubun PDL'lerini, o ekip için kanal ileti verisi verilerin nerede depola ilgili olduğunu belirlemek için kullanır. Buna, kanal toplantısında yapılan özel kanallar ve sohbet de dahildir.

Bir kullanıcı yeni ekip oluşturduğunda, bu kullanıcının PDL'si yeni bir ekip grubuna hangi PDL'nin Microsoft 365 belirler. Bu ekibin verilerini depolandığı yeri PDL grubu belirler. Bu kullanıcının PDL'si daha sonra değişirse, grubun PDL'si değişmez.

Mevcut ekipler için, yönetici bir ekibi geri alan Microsoft 365 grubunun PDL'sini ekler veya değiştirebilirse, ekibin kanal mesajlaşma verileri belirtilen coğrafi konuma taşınmak üzere geçiş sırasına eklenir.

Microsoft 365 grubunun PDL'sini değiştirmek, seçilen Teams geçirilecek sırada sıraya geçirir. Ancak bu, Grupla ilişkilendirilmiş SharePoint siteyi veya dosyaları otomatik olarak geçirmez. Siteyi farklı bir coğrafi konuma taşıma SharePoint aşağıdaki yordamları [SharePoint, siteyi ayrı ayrı taşıabilirsiniz](/microsoft-365/enterprise/move-sharepoint-between-geo-locations). Verilerden kaçınmak ve farklı konumlarda Teams için SharePoint adımları uygulayın.

Bir ekibin verilerini geçerli konumunu bulmak için, [PowerShell'Teams bağlanın](/powershell/module/teams/connect-microsoftteams) ve aşağıdaki komutu çalıştırın:

```PowerShell
Get-MultiGeoRegion -EntityType Group -EntityId <GroupObjectId>
```

## <a name="user-experience"></a>Kullanıcı Deneyimi

Teams Multi-Geo son kullanıcı için sorunsuz olur. Bir kullanıcının veya grubun PDL'sini değiştirilnin ardından, ilgili veriler geçiş için sıraya başlar ve geçiş gerçekleşirken etkin olsalar bile kullanıcı veya Teams istemcisi üzerinde hiçbir etkisi olmaz.

## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 Multi-Geo kiracı yapılandırması](/microsoft-365/enterprise/multi-geo-tenant-configuration)

[Çok coğrafi ortamı yönetme](administering-a-multi-geo-environment.md)

[Çok Exchange Online ortamda posta kutularını yönetme](administering-exchange-online-multi-geo.md)
