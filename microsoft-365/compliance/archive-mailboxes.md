---
title: Uyumluluk için arşiv posta kutuları hakkında Microsoft 365 öğrenin
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.ArchivingHelp
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: Ek posta kutusu depolama alanı sağlamak için arşiv posta kutuları hakkında bilgi alın.
ms.openlocfilehash: a863df7be1b73d6a50d818bca5948f3017e3d373
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010849"
---
# <a name="learn-about-archive-mailboxes"></a>Arşiv posta kutuları hakkında bilgi alın

Aynı E-posta Microsoft 365 (Yerinde Arşivleme olarak da adlandırılan) posta kutusu *arşivleme*, kullanıcılara ek posta kutusu depolama alanı sağlar. Arşiv posta kutularını açtırdikten sonra, kullanıcının geçerli posta kutusu birincil posta kutusu olur  ve arşiv posta kutusu adı verilen başka bir *posta kutusu oluşturulur*. Her iki posta kutusu da Posta Kutusundan İçerik araması, bekletme süresi, Microsoft 365 uyumluluk merkezi Microsoft 365 Saklama gibi uyumluluk özellikleri için kullanıcının posta kutusu olarak kabul edilir.

Kullanıcılar, arşiv posta kutularına posta kutularına posta kutularına e-posta Outlook Web üzerinde Outlook. Kullanıcılar ayrıca, iletileri birincil posta kutularıyla arşiv posta kutuları arasında taşımak veya kopyalamak için de kullanabilir. Ayrıca, Silinmiş Öğeleri Kurtar aracını kullanarak, arşiv posta kutularıdaki Kurtarılabilir Öğeler klasöründeki silinmiş öğeleri de kurtarabilir.

## <a name="managing-archive-mailboxes-with-messaging-records-management-mrm"></a>Mesajlaşma Kayıtları Yönetimi (MRM) ile arşiv posta kutularını yönetme

İletiler, İleti Kayıtları Yönetimi'nin (MRM) varsayılan [bekletme Exchange](/exchange/security-and-compliance/messaging-records-management/default-retention-policy) arşiv posta kutusuna da taşınır. Bu varsayılan ilke her posta kutusuna otomatik olarak atanır ve şunları yapar:

  - İki yıllık veya daha eski öğeleri kullanıcının birincil posta kutusundan arşiv posta kutusuna taşır.

  - 14 günlük veya daha eski öğeleri kullanıcının birincil posta kutusunda kurtarılabilir Öğeler klasöründen arşiv posta kutusunun Kurtarılabilir Öğeler klasörüne taşır.

Bekletme etiketleriyle, kuruluş MRM ilkenizi [özelleştirebilirsiniz](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies). Örnek bir yapılandırma için bkz [. Kuruluşta posta kutuları için bir arşivleme ve silme ilkesi ayarlama](set-up-an-archive-and-deletion-policy-for-mailboxes.md).

> [!NOTE]
> BEKLETME ilkeleri ve bekletme Microsoft 365 gibi MRM de belirtilen süre sonrasında e-postaları otomatik olarak silebilir. MrM, bekletme Microsoft 365 daha eski bir teknoloji olduğu için, Uyumluluk uyumluluk ilkeleri ve bekletme etiketleriyle yan yana çalışmaya Microsoft 365 devam eder. Daha fazla bilgi için bkz [. Eski özellikler yerine bekletme ilkelerini ve bekletme etiketlerini kullanma](retention.md#use-retention-policies-and-retention-labels-instead-of-older-features).

## <a name="auto-expanding-archiving"></a>Otomatik genişleyen arşivleme 

Kullanıcının arşiv posta kutusu etkinleştirildikten sonra, 100 GB'a kadar ek depolama alanı kullanılabilir. Kullanıcıların daha fazla depolama alanına ihtiyacı varsa, arşiv posta kutularına 1,5 TB ek depolama alanı sağlamak için otomatik genişleyen arşivlemeyi etkinleştirin. Daha fazla bilgi için bkz[. Otomatik genişleyen arşivleme hakkında bilgi.](autoexpanding-archiving.md)

## <a name="licensing"></a>Lisanslama

Arşiv posta kutularını destekleyen Outlook lisanslarının listesi için bkz. In-Place Arşivleme'ye Outlook [için lisans gereksinimlerine Exchange bakın](https://support.microsoft.com/office/46b6b7c5-c3ca-43e5-8424-1e2807917c99).

## <a name="next-steps"></a>Sonraki adımlar

Bkz [. Uyumluluk merkezinde arşiv posta kutularını etkinleştirme](enable-archive-mailboxes.md).