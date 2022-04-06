---
title: Kasa, Bağlantı SharePoint OneDrive için Ekleri Microsoft Teams
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 26261670-db33-4c53-b125-af0662c34607
ms.collection:
- M365-security-compliance
- SPO_Content
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
description: SharePoint Online, OneDrive İş ve diğer OneDrive İş hakkında bilgi Microsoft Teams. Office 365 için Microsoft Defender
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 220bb976ebe701e5db5f03370a1a7c188f197cb1
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475773"
---
# <a name="safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>Kasa, Bağlantı SharePoint OneDrive için Ekleri Microsoft Teams

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Kasa SharePoint, OneDrive ve Microsoft Teams ekleri, [Office 365 için Microsoft Defender'te](whats-new-in-defender-for-office-365.md) ortak virüs algılama altyapısı tarafından zaman uyumsuz olarak taranmış dosyalar için ek bir koruma katmanı sağlar [ Microsoft 365](virus-detection-in-spo.md). Kasa. SharePoint, OneDrive ve Microsoft Teams ekleri, ekip sitelerinde ve belge kitaplıklarında kötü amaçlı olarak tanımlanan mevcut dosyaları algılamaya ve engellemeye yardımcı olur.

Kasa, SharePoint, OneDrive ve Microsoft Teams için ekler varsayılan olarak etkin değildir. Bu eklentiyi açmak için bkz[. Kasa, E-posta SharePoint OneDrive' Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md).

## <a name="how-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams-works"></a>E Kasa, SharePoint, OneDrive ve Microsoft Teams nasıl çalışır?

Kasa, SharePoint, OneDrive ve Microsoft Teams ekleri etkinleştirildiğinde ve bir dosyayı kötü amaçlı olarak tanımıyorsa, dosya depolarla doğrudan tümleştirme kullanılarak kilitlenir. Aşağıdaki resimde, kitaplıkta algılanan kötü amaçlı bir dosyanın örneği bulunmaktadır.

:::image type="content" source="../../media/2bba71cc-7ad1-4799-8b9d-d56f923db3a7.png" alt-text="Dosyada kötü OneDrive İş biri ile algılanan dosyalar" lightbox="../../media/2bba71cc-7ad1-4799-8b9d-d56f923db3a7.png":::

Engellenen dosya belge kitaplığında ve web, mobil veya masaüstü uygulamalarında listelenmiş olsa da, kişiler dosyayı açamıyor, kopyalayıp taşıyamıyor veya paylaşamıyor. Ancak engellenen dosyayı silebilirler.

İşte mobil cihazda engellenen dosyanın nasıl göründüğünün bir örneği:

:::image type="content" source="../../media/cb1c1705-fd0a-45b8-9a26-c22503011d54.png" alt-text="Engellenen dosyayı mobil uygulamadan OneDrive İş silme OneDrive seçeneği" lightbox="../../media/cb1c1705-fd0a-45b8-9a26-c22503011d54.png":::

Varsayılan olarak, kişiler engellenen bir dosyayı indirebilir. Engellenen bir dosyayı indirme işlemi mobil cihaza şöyle olur:

:::image type="content" source="../../media/be288a82-bdd8-4371-93d8-1783db3b61bc.png" alt-text="OneDrive İş'te engellenen bir dosyayı indirme OneDrive İş" lightbox="../../media/be288a82-bdd8-4371-93d8-1783db3b61bc.png":::

SharePoint Online yöneticileri kişilerin kötü amaçlı dosyaları indirmesini önlenebilir. Yönergeler için bkz. [SharePoint kötü amaçlı dosyaları indirmelerini engellemek için SharePoint Online PowerShell kullanma](turn-on-mdo-for-spo-odb-and-teams.md#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files).

Bir dosya kötü amaçlı olarak algılandığında kullanıcı deneyimi hakkında daha fazla bilgi edinmek için bkz. [SharePoint Online'da, OneDrive'de](https://support.microsoft.com/office/01e902ad-a903-4e0f-b093-1e1ac0c37ad2) veya başka bir Microsoft Teams.

## <a name="view-information-about-malicious-files-detected-by-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>Dosya, Dosya ve Dosya Ekleri Kasa tarafından algılanan kötü amaçlı dosyalar SharePoint OneDrive bilgileri Microsoft Teams

Kasa, SharePoint, OneDrive ve Microsoft Teams ekleri tarafından kötü amaçlı olarak tanımlanan dosyalar Office 365 için Microsoft Defender ve [Explorer'daki raporlarda (](threat-explorer.md)ve gerçek zamanlı algılamalar) gösterir.[](view-reports-for-mdo.md)

Dosya Kasa, SharePoint OneDrive ve Microsoft Teams ekleri ile kötü amaçlı olarak tanımlandısa, dosya karantinada da kullanılabilir, ancak yalnızca yöneticiler tarafından kullanılabilir. Daha fazla bilgi için bkz[. Karantinaya alınmış dosyaları tek tek Office 365 için Defender](manage-quarantined-messages-and-files.md#use-the-microsoft-365-defender-portal-to-manage-quarantined-files-in-defender-for-office-365).

## <a name="keep-these-points-in-mind"></a>Bu noktaları gözlerde tutma

- Office 365 için Defender, SharePoint Online, OneDrive İş veya Microsoft Teams'te tek tek Microsoft Teams. Bu, tasarımdan kaynaklanır. Dosyalar zaman uyumsuz olarak taranır. Bu işlemde, kötü amaçlı dosyaları tanımlamak için paylaşım ve konuk etkinliği etkinliklerinin yanı sıra akıllı heuristler ve tehdit işaretleri de kullanılır.

- En son SharePoint Modern deneyimi kullanmak üzere yapılandırıldığından [emin olun](/sharepoint/guide-to-sharepoint-modern-experience). Office 365 için Defender koruması Hem Modern deneyim hem de Klasik görünüm kullanılırken geçerlidir; bununla birlikte, bir dosyanın engellenmiş olduğu görsel göstergeler yalnızca Modern deneyimde kullanılabilir.

- Kasa SharePoint, OneDrive ve Microsoft Teams ekleri, Exchange Online Protection'te (EOP) istenmeyen posta ve kötü amaçlı yazılımdan koruma ile kötü amaçlı yazılımdan korumayı içeren genel tehdit koruma stratejisinde yer alan Kasa Bağlantılar'dır ve Kasa'de Ekleri Office 365 için Microsoft Defender. Daha fazla bilgi edinmek için bkz[. Güvenlik tehditlerine Office 365](protect-against-threats.md).
