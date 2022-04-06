---
title: Microsoft 365 Defender portalında ileti izleme
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: 3e64f99d-ac33-4aba-91c5-9cb4ca476803
ms.custom:
- seo-marvel-apr2020
description: Yöneticiler, iletilere ne olduğunu Microsoft 365 Defender portalda ileti izleme bağlantısını kullanabilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d09470e37c066202d49d7d79788c12853ed42e21
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63679752"
---
# <a name="message-trace-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında ileti izleme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

İleti izleme, e-posta iletilerini, e-posta Exchange Online izler. İletinin hizmet tarafından alınarak, reddedilmiş, ertelenmiş veya teslimilmiş olup olmadığını belirlersiniz. Ayrıca, son durumuna ulaşmadan önce ileti üzerinde hangi eylemlerin gerçekleştirildiklerini de gösterir.

İletilere ne olduğu, posta akışı sorunlarını giderme ve ilke değişikliklerini doğrulama konusunda kullanıcı sorularını etkili bir şekilde yanıtlamak için ileti izlemeden alınan bilgileri kullanabilirsiniz.

> [!NOTE]
> İleti izleme Microsoft 365 Defender, yönetim merkezinde İleti izleme'ye Exchange geçmektir. Daha fazla bilgi için [bkz. Modern yönetim merkezinde Exchange izleme](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- İleti izlemeyi kullanmak için bu grupta **yer alan Kuruluş Yönetimi****, Uyumluluk** **Yönetimi veya** **Yardım Masası rol Exchange Online** üyesi olmak gerekir. Daha fazla bilgi için bkz. [Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Notlar**: Toplantı sırasında ilgili Azure Active Directory rolüne Microsoft 365 yönetim merkezi kullanıcılara e-postayla ilgili diğer özellikler için gerekli izinleri  ve Microsoft 365. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).

- İleti izlemenin sonuçlarında en fazla görüntülenen ileti sayısı, seçtiğiniz rapor türüne bağlıdır (ayrıntılar için Rapor türünü [seçme bölümüne bakın](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac#choose-report-type) ). powershell veya tek başına EOP PowerShell Exchange Online [get-HistoricalSearch](/powershell/module/exchange/get-historicalsearch) cmdlet'i, sonuçlardaki tüm iletileri döndürür.

## <a name="open-message-trace"></a>İleti izlemeyi açma

aşağıdaki Microsoft 365 Defender portalında E-posta <https://security.microsoft.com>ve işbirliği **& ileti** \> **Exchange gidin**. Doğrudan ileti izleme sayfasına gitmek için , kullanın <https://admin.exchange.microsoft.com/#/messagetrace>.

Bu noktada, EAC'de ileti izleme açılır. Daha fazla bilgi için [bkz. Modern yönetim merkezinde Exchange izleme](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac).
