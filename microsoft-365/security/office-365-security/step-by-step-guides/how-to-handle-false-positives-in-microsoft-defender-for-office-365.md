---
title: (Hatalı PozitifLer) Office 365 için Microsoft Defender kullanarak teslimi engellenen geçerli e-postaları işleme
description: İş kaybı yaşanmasını önlemek için Office 365 için Microsoft Defender tarafından engellenen geçerli e-postayı (Hatalı Pozitif) işleme adımları.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: jarogers
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: article
ms.technology: mdo
ms.openlocfilehash: 4a82bc32d1c41a3ee6e200e886cea4c325fadb02
ms.sourcegitcommit: 7ab324551afac4fd82abc015247371ebfe6ccac2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2022
ms.locfileid: "65842533"
---
# <a name="how-to-handle-legitimate-emails-getting-blocked-false-positive-using-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender kullanarak Engellenen geçerli e-postaları işleme (Hatalı Pozitif)

Office 365 için Microsoft Defender, yanlışlıkla tehdit olarak engellenen önemli meşru iş e-postalarıyla ilgilenmeye yardımcı olur (Hatalı Pozitifler). Office 365 için Defender yöneticilerin meşru e-postaların *neden* engellendiğini anlamasına, durumu hızla çözmesine ve gelecekte benzer durumların oluşmasını önlemesine yardımcı olabilir.

## <a name="what-youll-need"></a>İhtiyacınız olan şey

- Office 365 için Microsoft Defender Plan 1 veya 2 (E3, E5'in bir parçası olarak dahildir). EOP müşterileri de bu özellikten yararlanabilir.
- Yeterli izinler (Güvenlik Yöneticisi rolü).
- Aşağıdaki adımları gerçekleştirmek için 5-10 dakika.

## <a name="handling-legitimate-emails-in-to-junk-folder-of-end-users"></a>Son kullanıcıların Gereksiz klasöründeki geçerli e-postaları işleme

1. Son kullanıcılardan Microsoft İleti Eklentisi'ni veya Outlook düğmelerini kullanarak e-postayı **gereksiz değil** olarak bildirmelerini isteyin.
2. Son kullanıcılar, gereksiz klasörüne gelen bu [**gönderenlerden**](https://support.microsoft.com/en-us/office/safe-senders-in-outlook-com-470d4ee6-e3b6-402b-8cd9-a6f00eda7339) gelen e-postaları önlemek için Outlook'daki güvenilir gönderen listesine de göndereni ekleyebilir.
3. Yöneticiler, kullanıcı tarafından bildirilen içerik portalından [kullanıcı tarafından bildirilen](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#view-user-submissions-to-microsoft) iletileri önceliklendirme yapabilir.
4. Bu bildirilen iletilerden yöneticiler [**analiz için Microsoft'a**](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#notify-users-from-within-the-portal) gönderebilir ve bu e-postanın neden ilk etapta engellendiğini anlayabilir.
5. Gerekirse, yöneticiler analiz için Microsoft'a gönderirken, [ bir gönderenin](/microsoft-365/security/office-365-security/manage-tenant-allows?view=o365-worldwide#add-sender-allows-using-the-submissions-portal) sorunu hafifletebilmesi için bir izin oluşturabilir.
6. Yönetici gönderiminden elde edilen sonuçlar kullanıma sunulduktan sonra, e-postaların neden engellendiğini ve kiracı kurulumunuzun gelecekte benzer durumların *oluşmasını önlemek* için nasıl iyileştirilebileceğini anlamak için okuyun.

## <a name="handling-legitimate-emails-that-are-in-quarantine-folder-of-end-users"></a>Son kullanıcıların karantina klasöründeki geçerli e-postaları işleme

1. Son kullanıcı, güvenlik yöneticileri tarafından etkinleştirilen ayarlara göre karantinaya alınan iletiler hakkında [bir e-posta özeti](/microsoft-365/security/office-365-security/use-spam-notifications-to-release-and-report-quarantined-messages?view=o365-worldwide) alır.
2. Son kullanıcılar karantinadaki iletilerin önizlemesini görebilir, göndereni engelleyebilir, iletileri yayımlayabilir, bu iletileri analiz için Microsoft'a gönderebilir ve bu e-postaların yöneticilerden yayımlanmasını isteyebilir.

## <a name="handling-legitimate-emails-emails-in-quarantine-folder-of-an-admin"></a>Bir yöneticinin karantina klasöründeki geçerli e-posta e-postalarını işleme

1. Yöneticiler, karantinaya alınan e-postaları (yayın isteğinde bulunmak için izin isteyen e-postalar dahil) [gözden geçirme sayfasından](/microsoft-365/security/office-365-security/manage-quarantined-messages-and-files?view=o365-worldwide) görüntüleyebilir.
2. Yöneticiler, iletiyi analiz için Microsoft'a gönderirken karantinadan gönderebilir ve durumu azaltmak için bir izin oluşturabilir.
3. Gönderim sonuçları kullanıma sunulduktan sonra, yöneticilerin e-postaların neden engellendiğini ve gelecekte benzer durumların oluşmasını önlemek için kiracı kurulumunun nasıl iyileştirilebileceğini anlamak için kararı okuması gerekir.