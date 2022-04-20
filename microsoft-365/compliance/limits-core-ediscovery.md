---
title: eBulma (Standart) durumundaki sınırlar
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
description: Bu makalede, Microsoft 365'deki eBulma (Standart) durumundaki sınırlar açıklanmaktadır.
ms.openlocfilehash: 4eb43687e92d90179ff24d69827c3c2889d82b47
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971548"
---
# <a name="limits-in-ediscovery-standard"></a>eBulma sınırları (Standart)

Aşağıdaki tabloda, eBulma (Standart) durumlarının ve eBulma (Standart) servis talebiyle ilişkili tutmaların sınırları listeleniyor. Microsoft Purview eKeşif (Standart) hakkında daha fazla bilgi için bkz. [eKeşif'e Genel Bakış (Standart)](./get-started-core-ediscovery.md).
    
  | Sınırın açıklaması | Sınırı |
  |:-----|:-----|
  |Bir kuruluş için en fazla servis talebi sayısı.  <br/> |Sınır yok  <br/> |
  |Bir kuruluş için en fazla servis talebi tutma sayısı.  <br/> |10,000  <br/> |
  |Tek bir servis talebi ayrı tutmadaki en fazla posta kutusu sayısı. Bu sınır, kullanıcı posta kutularının toplamını ve Microsoft 365 Grupları, Microsoft Teams ve Yammer Grupları ile ilişkili posta kutularını içerir.  <br/> |1,000  <br/> |
  |Tek bir servis talebi saklamadaki en fazla site sayısı. Bu sınır, OneDrive İş sitelerin, SharePoint sitelerin ve Microsoft 365 Grupları, Microsoft Teams ve Yammer Grupları ile ilişkili sitelerin toplamını içerir.  <br/> |100  <br/> |
  |eBulma (Standart) giriş sayfasında görüntülenen en fazla servis talebi sayısı ve servis talebi içindeki Ayrı Tutmalar, Aramalar ve Dışarı Aktarma sekmelerinde görüntülenen en fazla öğe sayısı. <sup>1</sup> |1,000|

   > [!NOTE]
   > <sup></sup> 1.000'den fazla servis talebi, ayrı tutma, arama veya dışarı aktarma listesini görüntülemek için ilgili Office 365 Güvenlik & Uyumluluğu PowerShell cmdlet'lerini kullanabilirsiniz:
   > 
   > - [Get-ComplianceCase](/powershell/module/exchange/get-compliancecase)
   > - [Get-CaseHoldPolicy](/powershell/module/exchange/get-caseholdpolicy)
   > - [Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)
   > - [Get-ComplianceSearchAction](/powershell/module/exchange/get-compliancesearchaction)

eBulma (Standart) olayıyla ilişkili aramalar ve dışarı aktarmalarla ilgili sınırlar hakkında daha fazla bilgi için bkz. [İçerik arama ve eBulma (Standart) sınırları](limits-for-content-search.md).