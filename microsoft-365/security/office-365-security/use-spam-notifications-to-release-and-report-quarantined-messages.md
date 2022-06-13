---
title: Microsoft 365'de bildirimleri (son kullanıcı istenmeyen posta bildirimleri) karantinaya alın
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
description: Yöneticiler, Exchange Online Protection(EOP) içinde karantinaya alınan iletiler için son kullanıcı istenmeyen posta bildirimleri hakkında bilgi edinebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 44ed83a95fe8f588369f0a1bbae4809f32581f87
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/13/2022
ms.locfileid: "66043483"
---
# <a name="use-quarantine-notifications-to-release-and-report-quarantined-messages"></a>Karantinaya alınan iletileri serbest bırakmak ve bildirmek için karantina bildirimlerini kullanma

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online posta kutusu olmayan Exchange Online veya tek başına Exchange Online Protection (EOP) kuruluşlarında posta kutuları olan Microsoft 365 kuruluşlarda karantina, potansiyel olarak tehlikeli veya istenmeyen iletileri barındırıyor. Daha fazla bilgi için bkz. [EOP'de karantinaya alınan iletiler](quarantine-email-messages.md).

_Karantina ilkeleri_ , kullanıcıların karantinaya alınan iletilere ne yapmalarına izin verildiğini, iletinin neden karantinaya alındığına (desteklenen özellikler için) göre tanımlar. Daha fazla bilgi için bkz [. Karantina ilkeleri](quarantine-policies.md). Karantina ilkeleri, etkilenen alıcıların (paylaşılan posta kutuları dahil) karantinaya alınan iletileriyle ilgili düzenli _karantina bildirimleri_ alıp almadığını da denetler. Karantina bildirimleri, tüm desteklenen koruma özellikleri (yalnızca istenmeyen posta önleme ilkesi kararları değil) için son kullanıcı istenmeyen posta bildirimlerinin yerini alır.

AdminOnlyAccessPolicy veya DefaultFullAccessPolicy adlı yerleşik karantina bildirimlerinde karantina bildirimleri açık değildir. [Kuruluşunuzda varsa](quarantine-policies.md#full-access-permissions-and-quarantine-notifications) NotificationEnabledPolicy adlı yerleşik karantina ilkesinde karantina bildirimleri açılır. Aksi takdirde, karantina ilkelerinde karantina bildirimlerini açmak için [yeni bir karantina ilkesi oluşturmanız ve yapılandırmanız](quarantine-policies.md#step-1-create-quarantine-policies-in-the-microsoft-365-defender-portal) gerekir.

Ayrıca, karantina bildirimlerinde 'Göndereni engelle' seçeneğinin düzgün çalışmasına izin vermek için kullanıcıların uzak Powershell için etkinleştirilmesi gerekir. Yönergeler için bkz[. Exchange Online PowerShell'e erişimi etkinleştirme veya devre dışı bırakma](/powershell/exchange/disable-access-to-exchange-online-powershell).

Yöneticiler ayrıca karantina ilkelerindeki genel ayarları kullanarak gönderenin görünen adını, farklı dillerdeki yasal uyarı metnini ve karantina bildirimlerinde kullanılan şirket logosunu özelleştirebilir. Yönergeler için bkz [. Genel karantina bildirimi ayarlarını yapılandırma](quarantine-policies.md#configure-global-quarantine-notification-settings-in-the-microsoft-365-defender-portal).

Paylaşılan posta kutuları için karantina bildirimleri yalnızca paylaşılan posta kutusuna FullAccess izni verilen kullanıcılar için desteklenir. Daha fazla bilgi için bkz. [Paylaşılan posta kutusu temsilcisini düzenlemek için EAC kullanma](/Exchange/collaboration-exo/shared-mailboxes#use-the-eac-to-edit-shared-mailbox-delegation).

> [!NOTE]
> Varsayılan olarak, yüksek güvenilirlikli kimlik avı, kötü amaçlı yazılım, posta akışı kuralları (aktarım kuralları olarak da bilinir) veya Office 365 için Defender Kasa Ekler ilkeleri olarak karantinaya alınan iletiler yalnızca yöneticiler tarafından kullanılabilir (varsayılan olarak AdminOnlyAccessPolicy karantina ilkesi kullanılır). Daha fazla bilgi için bkz. [Karantinaya alınan iletileri ve dosyaları EOP'de yönetici olarak yönetme](manage-quarantined-messages-and-files.md).
>
> Dağıtım gruplarına veya posta etkin güvenlik gruplarına gönderilen iletiler için karantina bildirimleri tüm grup üyelerine gönderilir.
>
> Microsoft 365 Grupları gönderilen iletiler için karantina bildirimleri, yalnızca **Grup konuşmalarının ve olaylarının kopyalarını grup** üyelerine gönder ayarı açıksa tüm grup üyelerine gönderilir.

Karantina bildirimi aldığınızda, karantinaya alınan her ileti için her zaman aşağıdaki bilgiler kullanılabilir:

- **Gönderen**: Karantinaya alınan iletinin gönderme adı ve e-posta adresi.
- **Konu**: Karantinaya alınan iletinin konu satırı metni.
- **Tarih**: İletinin karantinaya alındığı tarih ve saat (UTC olarak).

Karantina bildiriminde kullanılabilen eylemler, iletinin neden karantinaya alındığına ve ilişkili karantina ilkesi tarafından atanan izinlere bağlıdır. Daha fazla bilgi için bkz [. Karantina ilkesi izin ayrıntıları](quarantine-policies.md#quarantine-policy-permission-details).

Varsayılan olarak, istenmeyen posta, yüksek güvenilirlikli istenmeyen posta veya toplu olarak karantinaya alınan iletiler için karantina bildiriminde aşağıdaki eylemler kullanılabilir:

- **Göndereni Engelle**: Göndereni _posta_ kutunuzdaki Engellenen Gönderenler listesine eklemek için bu bağlantıya tıklayın. Daha fazla bilgi için bkz [. Posta göndereni engelleme](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).
- **Yayın**: İletiyi Microsoft 365 Defender portalında **Karantinaya** Al'a gitmeden buradan yayımlayabilirsiniz.
- **Gözden Geçir**: Microsoft 365 Defender portalında **Karantinaya Al'a** gitmek için bu bağlantıya tıklayın; burada (iletinin neden karantinaya alındığına bağlı olarak) karantinaya alınan iletilerinizi görüntüleyebilir, yayımlayabilir, silebilir veya raporlayabilirsiniz. Daha fazla bilgi için bkz. [Karantinaya alınan iletileri EOP'de kullanıcı olarak bulma ve bırakma](find-and-release-quarantined-messages-as-a-user.md).

:::image type="content" source="../../media/end-user-spam-notification.png" alt-text="Karantina bildirimi örneği" lightbox="../../media/end-user-spam-notification.png":::

> [!NOTE]
> Engellenen bir gönderen size posta göndermeye devam edebilir. Bu gönderenden gelen ve posta kutunuza gönderen tüm iletiler hemen Gereksiz E-posta klasörüne taşınır. Bu gönderenden gelecek iletiler Gereksiz E-posta klasörünüze veya karantinaya alınacaktır. Bu iletilerin yerine vardığınızda silinmesini istiyorsanız, gelen iletileri silmek için [posta akışı kurallarını](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) (taşıma kuralları olarak da bilinir) kullanın.
