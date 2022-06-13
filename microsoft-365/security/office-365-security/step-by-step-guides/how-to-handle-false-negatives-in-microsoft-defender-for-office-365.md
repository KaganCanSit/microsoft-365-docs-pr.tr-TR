---
title: (Yanlış Negatifler) Office 365 için Microsoft Defender kullanılarak alıcılara teslim edilen kötü amaçlı e-postalar ile nasıl başa çıkılır?
description: İş kaybını önlemek için son kullanıcılara ve gelen kutularına gelen kötü amaçlı e-postaları (Hatalı Negatifler olarak) Office 365 için Microsoft Defender ile işleme adımları.
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
ms.topic: how-to
ms.technology: mdo
ms.openlocfilehash: decbece049ea4f91deb529d2fd640816bf3f1d0c
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/13/2022
ms.locfileid: "66042156"
---
# <a name="how-to-handle-malicious-emails-that-are-delivered-to-recipients-false-negatives-using-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender kullanarak alıcılara teslim edilen kötü amaçlı e-postaları işleme (Hatalı Negatifler)

Office 365 için Microsoft Defender, alıcılara teslim edilen ve kurumsal üretkenliğinizi riske soan kötü amaçlı e-postalarla (Hatalı Negatif) başa çıkmanıza yardımcı olur.
Office 365 için Defender e-postaların neden teslim alınıyor olduğunu, durumu hızla nasıl çözeceğinizi ve gelecekte benzer durumların oluşmasını nasıl önleyeceğinizi anlamanıza yardımcı olabilir.

## <a name="what-youll-need"></a>İhtiyacınız olan şey

- Office 365 için Microsoft Defender Plan 1 ve 2 (E5'in bir parçası olarak dahildir). Exchange Online müşteriler de bundan yararlanabilir.
- Yeterli izinler (Güvenlik Yöneticisi rolü).
- Aşağıdaki adımları gerçekleştirmek için 5-10 dakika.

## <a name="handling-malicious-emails-in-the-inbox-folder-of-end-users"></a>Son kullanıcıların Gelen Kutusu klasöründe kötü amaçlı e-postaları işleme

1. Son kullanıcılardan Microsoft İleti Eklentisi veya Microsoft Kimlik Avı eklentisini veya Outlook düğmelerini kullanarak e-postayı **kimlik avı** veya **gereksiz** olarak bildirmelerini isteyin.
2. Son kullanıcılar, bu gönderenden gelen e-postaların gelen kutularına teslim edilmesini önlemek için Outlook'daki [engellenen gönderenler listesine](https://support.microsoft.com/en-us/office/block-a-mail-sender-b29fd867-cac9-40d8-aed1-659e06a706e4#:~:text=1%20On%20the%20Home%20tab%2C%20in%20the%20Delete,4%20Click%20OK%20in%20both%20open%20dialog%20boxes..) de göndereni ekleyebilir.
3. Yöneticiler, kullanıcı tarafından bildirilen [iletileri kullanıcı tarafından bildirilen içerik](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#view-user-submissions-to-microsoft&preserve-view=true) portalından önceliklendirme yapabilir.
4. Bu bildirilen iletilerden yöneticiler, bu e-postaya neden izin verildiğini öğrenmek [için analiz için Microsoft'a](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#notify-users-from-within-the-portal&preserve-view=true) **gönderebilir**.
5. Gerekirse, yöneticiler analiz için Microsoft'a gönderirken [, gönderenin](/microsoft-365/security/office-365-security/manage-tenant-blocks?view=o365-worldwide&preserve-view=true) sorunu azaltması için bir blok oluşturabilir.
6. Gönderim sonuçları kullanıma sunulduktan sonra, e-postalara neden izin verildiğini ve gelecekte benzer durumların oluşmasını önlemek için kiracı kurulumunuzun nasıl iyileştirilebileceğini anlamak için kararı okuyun.

## <a name="handling-malicious-emails-in-junk-folder-of-end-users"></a>Son kullanıcıların gereksiz klasöründeki kötü amaçlı e-postaları işleme

1. Son kullanıcılardan Microsoft İleti Eklentisi veya Microsoft Kimlik Avı Eklentisi veya Outlook düğmelerini kullanarak e-postayı **kimlik avı** olarak bildirmelerini isteyin.
2. Yöneticiler, kullanıcı tarafından bildirilen içerik portalından bildirilen iletileri önceliklendirmek için [kullanabilir](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#view-user-submissions-to-microsoft&preserve-view=true) .
3. Bu bildirilen iletilerden yöneticiler [analiz için Microsoft'a](/microsoft-365/security/office-365-security/admin-submission?view=o365-worldwide#notify-users-from-within-the-portal&preserve-view=true) **gönderebilir** ve bu e-postaya neden izin verildiğini ilk etapta öğrenebilir.
4. Gerekirse, yöneticiler analiz için Microsoft'a gönderirken [, gönderenin](/microsoft-365/security/office-365-security/manage-tenant-blocks?view=o365-worldwide&preserve-view=true) sorunu azaltması için bir blok oluşturabilir.
5. Gönderim sonuçları kullanıma sunulduktan sonra, e-postalara neden izin verildiğini ve gelecekte benzer durumların oluşmasını önlemek için kiracı kurulumunuzun nasıl iyileştirilebileceğini anlamak için kararı okuyun.

## <a name="handling-malicious-emails-landing-in-the-quarantine-folder-of-end-users"></a>Son kullanıcıların karantina klasörüne inen kötü amaçlı e-postaları işleme

1. Son kullanıcılar, yöneticilerin etkinleştirdiği ayarlara göre karantinaya alınan iletiler hakkında bir [e-posta özeti](/microsoft-365/security/office-365-security/use-spam-notifications-to-release-and-report-quarantined-messages?view=o365-worldwide&preserve-view=true) alır.
2. Son kullanıcılar karantinadaki iletilerin önizlemesini görebilir, göndereni engelleyebilir ve bu iletileri analiz için Microsoft'a gönderebilir.

## <a name="handling-malicious-emails-landing-in-the-quarantine-folder-of-admins"></a>Yöneticilerin karantina klasörüne inen kötü amaçlı e-postaları işleme

1. Yöneticiler, karantinaya alınan e-postaları (yayın isteğinde bulunmak için izin isteyen e-postalar dahil) [gözden geçirme sayfasından](/microsoft-365/security/office-365-security/manage-quarantined-messages-and-files?view=o365-worldwide&preserve-view=true) görüntüleyebilir.
2. Yöneticiler analiz için Microsoft'a kötü amaçlı veya şüpheli iletiler gönderebilir ve kararı beklerken durumu azaltmak için bir engel oluşturabilir.
3. Gönderim sonuçları kullanıma sunulduktan sonra, e-postalara neden izin verildiğini ve gelecekte benzer durumların yaşanmasını önlemek için kiracı kurulumunuzun nasıl iyileştirilebileceğini öğrenmek için kararı okuyun.
