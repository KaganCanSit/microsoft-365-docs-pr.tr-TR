---
title: E-postada bildirimleri karantinaya alın (son kullanıcı istenmeyen posta Microsoft 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: 56de4ed5-b0aa-4195-9f46-033d7cc086bc
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Yöneticiler, Exchange Online Protection(EOP) içinde karantinaya alınmış iletiler için son kullanıcı istenmeyen posta bildirimleri hakkında bilgi edinebilirsiniz.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 1950104e910733bfb3f846ff53411a6c75bbd68d
ms.sourcegitcommit: 2ea2105d40b60a87fc9aa30f392a73a3a9db6d99
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2021
ms.locfileid: "63007645"
---
# <a name="use-quarantine-notifications-to-release-and-report-quarantined-messages"></a>Karantinaya alınmış iletileri serbest bırakmak ve rapor etmek için karantina bildirimlerini kullanma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft 365 posta kutusu olmayan Exchange Online ya da tek başına Exchange Online Protection Exchange Online Protection EOP Exchange Online) kuruluşlarında, karantinada tehlikeli veya istenmeyen iletiler karantinaya alın. Daha fazla bilgi için bkz. [EOP'de karantinaya alınmış iletiler](quarantine-email-messages.md).

_Karantina ilkeleri_ , iletinin neden karantinaya alındığına (desteklenen özellikler için) dayalı olarak, kullanıcıların karantinaya alınmış iletilerde ne yapmalarına izin verilmiyor? Daha fazla bilgi için bkz. [Karantina ilkeleri](quarantine-policies.md). Karantina İlkeleri, etkilenen alıcıların (paylaşılan posta kutuları dahil) karantinaya alınmış iletileriyle ilgili düzenli olarak karantina _bildirimleri alınıp_ alınmayacaklarını da kontrol altına alır. Karantina bildirimleri, tüm desteklenen koruma özellikleri (yalnızca istenmeyen posta önleme ilkesi kararlarını değil) için son kullanıcı istenmeyen posta bildirimlerinin yerini alır.

AdminOnlyAccessPolicy veya DefaultFullAccessPolicy adlı yerleşik karantina bildirimlerde karantina bildirimleri açık değildir. Kuruluşta varsa, NotificationEnabledPolicy adlı yerleşik karantina ilkesinde karantina [bildirimleri açık olur](quarantine-policies.md#full-access-permissions-and-quarantine-notifications). Bunun dışında, karantina ilkeleri içinde karantina bildirimlerini açmak için, yeni bir [karantina ilkesi oluşturmanız ve yapılandırmanız gerekir](quarantine-policies.md#step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal).

Ayrıca, karantina bildirimlerinde 'Göndereni engelle' seçeneğinin doğru çalışmasına izin vermek için, kullanıcıların uzak Powershell'de etkinleştirilmesi gerekir. Yönergeler için bkz. [Exchange Online PowerShell'e erişimi etkinleştirme veya devre dışı bırakma](/powershell/exchange/disable-access-to-exchange-online-powershell).

Yöneticiler ayrıca karantina ilkelerinde genel ayarları kullanarak gönderenin görünen adını özelleştirilebilir, farklı dillerdeki bildirimi ve karantina bildirimlerinde kullanılan şirket logosunu özelleştirilebilir. Yönergeler için Bkz. [Genel karantina bildirim ayarlarını yapılandırma](quarantine-policies.md#configure-global-quarantine-notification-settings-in-the-microsoft-365-defender-portal).

Paylaşılan posta kutularda, karantina bildirimleri yalnızca paylaşılan posta kutusu için FullAccess izni verilen kullanıcılar için kullanılabilir. Daha fazla bilgi için bkz. [Paylaşılan posta kutusu temsilcilerini düzenlemek için EAC kullanma](/Exchange/collaboration-exo/shared-mailboxes#use-the-eac-to-edit-shared-mailbox-delegation).

> [!NOTE]
> Varsayılan olarak, Office 365 için Defender'daki posta akışı kuralları (aktarım kuralları olarak da bilinir) veya Kasa Ekler ilkeleri tarafından yüksek güven amaçlı kimlik avı, kötü amaçlı yazılım olarak karantinaya alınmış iletiler yalnızca yöneticiler tarafından kullanılabilir (varsayılan olarak, AdminOnlyAccessPolicy karantina ilkesi kullanılır). Daha fazla bilgi için bkz [. EOP'de yönetici olarak karantinaya alınmış iletileri ve dosyaları yönetme](manage-quarantined-messages-and-files.md).
>
> Şu anda, gruplar veya yüksek güvene sahip kimlik avı iletileri için karantina bildirimleri desteklenmiyor. 

Karantina bildirimi alırsanız, karantinaya alınan her ileti için aşağıdaki bilgiler her zaman kullanılabilir:

- **Gönderen**: Karantinaya alınan iletinin gönderme adı ve e-posta adresi.
- **Konu**: Karantinaya alınmış iletinin konu satırı metni.
- **Tarih**: İletinin karantinaya alındığı tarih ve saat (UTC).

Karantina bildiriminde kullanılabilen eylemler, iletinin neden karantinaya alındığına ve ilişkili karantina ilkesi tarafından atanan izinlere bağlıdır. Daha fazla bilgi için bkz [. Karantina ilkesi izin ayrıntıları](quarantine-policies.md#quarantine-policy-permission-details).

Varsayılan olarak, istenmeyen posta, yüksek güvene sahip istenmeyen posta veya toplu olarak karantinaya alınmış iletiler için karantina bildiriminde aşağıdaki eylemler kullanılabilir:

- **Göndereni** Engelle: Göndereni posta kutunuzda Engellenen Gönderenler listesine eklemek için bu _bağlantıya_ tıklayın. Daha fazla bilgi için bkz [. Posta göndereni engelleme](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).
- **Sürüm**: İletiyi, bu portalda Karantina'ya **Microsoft 365 Defender** çıkarabilirsiniz.
- **Gözden** Geçir: karantinaya alınmış iletilerinizi  görüntülemenize, bırakmanıza, silmenize veya bildirmenize izin verilecek şekilde Microsoft 365 Defender portalında Karantina'ya gitmek için bu bağlantıya tıklayın. Daha fazla bilgi için bkz [. EOP'de kullanıcı olarak karantinaya alınmış iletileri bulma ve serbest bırakma](find-and-release-quarantined-messages-as-a-user.md).

![Karantina bildirimi örneği.](../../media/end-user-spam-notification.png)

> [!NOTE]
> Engellenen bir gönderen yine de size posta gönderebilir. Bu gönderenden gelen ve posta kutunuza gönderen tüm iletiler hemen Gereksiz E-posta klasörüne taşınır. Gelecekte bu gönderenden gelen iletiler Gereksiz E-posta klasörünüze veya karantinaya gönderilir. Var olan iletileri var olanda kullanmak yerine silmek tercih ediyorsanız, varışda iletileri silmek için posta akış [kurallarını (aktarım](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) kuralları olarak da bilinir) kullanın.
