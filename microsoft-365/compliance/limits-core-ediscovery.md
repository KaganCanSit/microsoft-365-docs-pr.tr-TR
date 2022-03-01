---
title: Temel eKbulma durumunda sınırlar
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Bu makalede, Microsoft 365'de çekirdek eKbulma durumundaki sınırlar açık Microsoft 365.
ms.openlocfilehash: 28db179aea27bfff2520199d89b93c8260b7f089
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63033343"
---
# <a name="limits-in-core-ediscovery"></a>Çekirdek eKbulma sınırlamaları

Aşağıdaki tabloda, çekirdek eBulma servis durumlarının ve temel bir eKbulma durumuyla ilişkilendirilmiş askıyaların sınırları listelemektedir. Core eKovery hakkında daha fazla bilgi için bkz. [Core eKover'a Genel Bakış](./get-started-core-ediscovery.md).
    
  | Sınırın açıklaması | Sınır |
  |:-----|:-----|
  |Bir kuruluş için en fazla vaka sayısı.  <br/> |Sınır yok  <br/> |
  |Bir kuruluş için en fazla büyük büyük//veya daha fazla 12/sn.  <br/> |10,000  <br/> |
  |Tek bir durumdaki posta kutusu sayısı üst sayısı. Bu sınır, birleştirilmiş toplam kullanıcı posta kutusu ve Kullanıcı Grupları, Posta Microsoft 365, Posta Kutusu Microsoft Teams posta Yammer içerir.  <br/> |1,000  <br/> |
  |Tek bir vakada en fazla site sayısı. Bu sınır, birleştirilmiş toplam OneDrive İş sitesi, SharePoint sitesi ve Microsoft 365 Grupları, Site Grupları, Microsoft Teams ve Yammer içerir.  <br/> |100  <br/> |
  |Çekirdek eBulma giriş sayfasında görüntülenen vaka sayısı üst sayısı ve olaydaki 10/1000 ve Üzerinde Arama ve Dışarı Aktar sekmelerinde görüntülenen en fazla öğe sayısı. <sup>1</sup> |1,000|
  |||

   > [!NOTE]
   > <sup>1</sup> 1.000'den fazla olay, 1000'den fazla olay, arama veya dışarı aktarmanın listesini görüntülemek için ilgili Office 365 Güvenlik ve Uyumluluk PowerShell & cmdlet'lerini kullanabilirsiniz:
   > 
   > - [Get-ComplianceCase](/powershell/module/exchange/get-compliancecase)
   > - [Get-CaseHoldPolicy](/powershell/module/exchange/get-caseholdpolicy)
   > - [Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)
   > - [Get-ComplianceSearchAction](/powershell/module/exchange/get-compliancesearchaction)

Çekirdek eBulma durumuyla ilişkilendirilmiş aramalar ve dışarı aktarmalarla ilgili sınırlar hakkında daha fazla bilgi için bkz. İçerik arama ve [Çekirdek eBulma sınırları](limits-for-content-search.md).