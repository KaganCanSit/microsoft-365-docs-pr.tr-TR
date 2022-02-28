---
title: SharePoint Online, OneDrive ve Microsoft Teams'te yerleşik virüs koruması
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: reference
ms.localizationpriority: medium
search.appverid:
- SPO160
- MOE150
- MET150
ms.assetid: e3c6df61-8513-499d-ad8e-8a91770bff63
ms.collection:
- M365-security-compliance
description: SharePoint Online'ın, kullanıcıların karşıya yükledikten sonra dosyalarda virüsleri nasıl algılayanı ve kullanıcıların dosyaları indirmesini veya eşitlemesini nasıl önley olduğunu öğrenin.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ddb424458e991becefb98efbad5b2a86c5f9441c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988721"
---
# <a name="built-in-virus-protection-in-sharepoint-online-onedrive-and-microsoft-teams"></a>SharePoint Online, OneDrive ve Microsoft Teams'te yerleşik virüs koruması

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)

Microsoft 365 kullanıcıların SharePoint Online, dosya ve klasörlerine yükledikten sonra karşıya yükledikten sonra OneDrive algılama Microsoft Teams. Bu koruma, SharePoint Online, OneDrive ve diğer abonelikleri Microsoft Teams.

> [!IMPORTANT]
> Yerleşik virüsten koruma özellikleri virüs içermeye yardımcı olur. Bunlar ortamınız için kötü amaçlı yazılımlara karşı tek bir savunma noktası olarak hedefli değil. Tüm müşterilerin çeşitli katmanlar üzerinde kötü amaçlı yazılımdan korumayı araştırmalarını ve uygulamalarını ve kurumsal altyapılarının güvenliğini sağlamak için en iyi uygulamaları uygulamalarını teşvik ediyoruz. Stratejiler ve en iyi yöntemler hakkında daha fazla bilgi için bkz. [Güvenlik yol haritası](security-roadmap.md).

## <a name="what-happens-if-an-infected-file-is-uploaded-to-sharepoint-online"></a>Virüs bulaşmış bir dosya SharePoint Online'a yüklerse ne olur?

En Microsoft 365 algılama altyapısı, SharePoint Online'da zaman uyumsuz çalışır (dosya yüklemelerinden bağımsız olarak). **Tüm dosyalar otomatik olarak taranmaz**. Heuristics determine the files to scan. Virüs içeren bir dosya bulunduğu zaman, dosya bayrakla işaretlenir. Nisan 2018'de taranan dosyalar için 25 MB sınırını kaldırdık.

Neler olduğunu buradalarız:

1. Kullanıcı dosyayı SharePoint Online'a yükledi.
2. SharePoint Online, virüs tarama işlemlerinin bir parçası olarak dosyanın tarama ölçütüne uygun olup olmadığını belirler.
3. Dosya tarama ölçütüne uygunsa, virüs algılama altyapısı dosyayı tarar.
4. Taranan dosyanın içinde bir virüs bulunursa, virüs altyapısı dosyada virüs bulaştığını belirten bir özellik ayarlar.

## <a name="what-happens-when-a-user-tries-to-download-an-infected-file-by-using-the-browser"></a>Kullanıcı tarayıcıyı kullanarak virüslü bir dosya indirmeye çalıştığında ne olur?

Bir dosyanın virüsü bulaşırsa, kullanıcılar tarayıcı kullanarak SharePoint Online'dan dosyayı indirer.

Neler olduğunu buradalarız:

1. Bir kullanıcı web tarayıcısını açar ve SharePoint Online'dan virüs bulaşmış bir dosyayı indirmeye çalışır.
2. Kullanıcıya virüs algılandı uyarısı verilir. Varsayılan olarak, kullanıcıya dosyayı indirme ve kendi cihazında virüsten koruma yazılımını kullanarak temizlemeyi deneme seçeneği vardır.

> [!NOTE]
>
> Yöneticiler, kullanıcıların virüs önleme uyarı penceresinde bile virüs bulan dosyaları indirmelerini önlemek için SharePoint Online PowerShell'de [Set-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant) cmdlet'inde *DisallowInfectedFileDownload* parametresini kullanabilir. Yönergeler için bkz. [SharePoint kötü amaçlı dosyaları indirmelerini engellemek için SharePoint Online PowerShell kullanma](turn-on-mdo-for-spo-odb-and-teams.md#step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files).
>
> *DisallowInfectedFileDownload* parametresini etkinleştirir etkinleştirmez, kullanıcılar ve yöneticiler için algılanan/engellenen dosyalara erişim tamamen engellenir.

## <a name="what-happens-when-the-onedrive-sync-client-tries-to-sync-an-infected-file"></a>İstemci bulaşarak OneDrive eşitleme bir dosyayı eşitlemeye çalıştığında ne olur?

Kötü amaçlı bir dosya karşıya OneDrive, kötü amaçlı yazılım olarak işaretlenene kadar yerel makineyle eşitlenir. Kötü amaçlı yazılım olarak işaretlendikten sonra, kullanıcı eşitlenen dosyayı artık yerel makineden açamaz.

## <a name="extended-capabilities-with-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender ile genişletilmiş Office 365

Microsoft 365 için [Microsoft Office 365 Defender'ı](defender-for-office-365.md) aboneliğe dahil olan veya eklenti olarak satın alan Kasa kuruluşları, gelişmiş raporlama ve koruma için SharePoint, OneDrive ve Microsoft Teams eklerini etkinleştirebilirsiniz. Daha fazla bilgi için bkz[. Kasa, Dosya ve SharePoint OneDrive Ekleri'Microsoft Teams](mdo-for-spo-odb-and-teams.md).

## <a name="related-articles"></a>İlgili Makaleler

[Microsoft 365'te kötü amaçlı yazılım ve fidye yazılımına Microsoft 365](/compliance/assurance/assurance-malware-and-ransomware-protection)

SharePoint Online, OneDrive ve Microsoft Teams'de virüsten koruma hakkında daha fazla bilgi için bkz. Tehditlere karşı koruma ve SharePoint, [](protect-against-threats.md) OneDrive ve diğer Kasa [eklerini Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md).
