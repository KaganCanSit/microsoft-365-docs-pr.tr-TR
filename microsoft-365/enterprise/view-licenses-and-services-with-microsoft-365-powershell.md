---
title: PowerShell ile Microsoft 365 lisansları ve hizmetleri görüntüleme
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: Microsoft 365 kuruluşunuzda bulunan lisans planları, hizmetler ve lisanslar hakkındaki bilgileri görüntülemek için PowerShell'in nasıl kullanılacağını açıklar.
ms.openlocfilehash: 1d0d514cc0d821e8958a35c3598b41554260716d
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091951"
---
# <a name="view-microsoft-365-licenses-and-services-with-powershell"></a>PowerShell ile Microsoft 365 lisansları ve hizmetleri görüntüleme

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Her Microsoft 365 aboneliği aşağıdaki öğelerden oluşur:

- **Lisanslama planları** Bunlar lisans planları veya Microsoft 365 planları olarak da bilinir. Lisans planları, kullanıcıların kullanabileceği Microsoft 365 hizmetlerini tanımlar. Microsoft 365 aboneliğiniz birden çok lisans planı içerebilir. Örnek bir lisans planı Microsoft 365 E3.
    
- **Hizmetleri** Bunlar hizmet planları olarak da bilinir. Hizmetler, Exchange Online ve Kurumlar için Microsoft 365 Uygulamaları (eski adıyla Office 365 ProPlus) gibi her lisans planında kullanılabilen Microsoft 365 ürünleri, özellikleri ve özellikleridir. Kullanıcılara farklı hizmetlere erişim izni veren farklı lisans planlarından atanmış birden çok lisans olabilir.
    
- **Lisans** Her lisans planı satın aldığınız lisans sayısını içerir. Lisans planı tarafından tanımlanan Microsoft 365 hizmetlerini kullanabilmeleri için kullanıcılara lisans atarsınız. Her kullanıcı hesabı, Microsoft 365 oturum açabilmesi ve hizmetleri kullanabilmesi için bir lisans planından en az bir lisans gerektirir.
    
Microsoft 365 kuruluşunuzdaki kullanılabilir lisans planları, lisanslar ve hizmetler hakkındaki ayrıntıları görüntülemek için Microsoft 365 için PowerShell'i kullanabilirsiniz. Farklı Office 365 aboneliklerinde kullanılabilen ürünler, özellikler ve hizmetler hakkında daha fazla bilgi için bkz. [Plan Seçenekleri Office 365](/office365/servicedescriptions/office-365-platform-service-description/office-365-plan-options).


## <a name="use-the-microsoft-graph-powershell-sdk"></a>Microsoft Graph PowerShell SDK'sını kullanma

İlk olarak [Microsoft 365 kiracınıza bağlanın](/graph/powershell/get-started#authentication).

Abonelik lisans planlarının okunması için Organization.Read.All izin kapsamı veya ['Abone olunanSkuları listele' Graph API başvuru sayfasında listelenen diğer izinlerden](/graph/api/subscribedsku-list) biri gerekir.

```powershell
Connect-Graph -Scopes Organization.Read.All
```

Geçerli lisans planlarınız ve her bir plan için kullanılabilir lisanslar hakkındaki özet bilgileri görüntülemek için şu komutu çalıştırın:
  
```powershell
Get-MgSubscribedSku | Select -Property Sku*, ConsumedUnits -ExpandProperty PrepaidUnits | Format-List
```

Sonuçlar aşağıdakileri içerir:
  
- **SkuPartNumber:** Kuruluşunuz için kullanılabilir lisans planlarını gösterir. Örneğin, `ENTERPRISEPACK` Office 365 Kurumsal E3 için lisans planı adıdır.
    
- **Etkin:** Belirli bir lisans planı için satın aldığınız lisansların sayısı.
    
- **ConsumedUnits:** Belirli bir lisans planındaki kullanıcılara atadığınız lisansların sayısı.
    
Tüm lisans planlarınızda kullanılabilen Microsoft 365 hizmetleriyle ilgili ayrıntıları görüntülemek için önce lisans planlarınızın listesini görüntüleyin.

```powershell
Get-MgSubscribedSku
```

Ardından lisans planları bilgilerini bir değişkende depolayın.

```powershell
$licenses = Get-MgSubscribedSku
```

Ardından hizmetleri belirli bir lisans planında görüntüleyin.

```powershell
$licenses[<index>].ServicePlans
```

\<index> , komutun görüntüsünden `Get-MgSubscribedSku | Select SkuPartNumber` lisans planının satır numarasını belirten bir tamsayıdır( eksi 1).

Örneğin, komutun `Get-MgSubscribedSku | Select SkuPartNumber` görüntüsü şuysa:

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

Ardından ENTERPRISEPREMIUM lisans planına yönelik hizmetleri görüntüleme komutu şu şekildedir:

```powershell
$licenses[2].ServicePlans
```

ENTERPRISEPREMIUM üçüncü satırdır. Bu nedenle, dizin değeri (3 - 1) veya 2'dir.

Lisans planlarının tam listesi (ürün adları olarak da bilinir), bunların dahil edilen hizmet planları ve bunlara karşılık gelen kolay adları için bkz. [Lisanslama için ürün adları ve hizmet planı tanımlayıcıları](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph için Azure Active Directory PowerShell modülünü kullanma

İlk olarak [Microsoft 365 kiracınıza bağlanın](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Geçerli lisans planlarınız ve her bir plan için kullanılabilir lisanslar hakkındaki özet bilgileri görüntülemek için şu komutu çalıştırın:
  
```powershell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

Sonuçlar aşağıdakileri içerir:
  
- **SkuPartNumber:** Kuruluşunuz için kullanılabilir lisans planlarını gösterir. Örneğin, `ENTERPRISEPACK` Office 365 Kurumsal E3 için lisans planı adıdır.
    
- **Etkin:** Belirli bir lisans planı için satın aldığınız lisansların sayısı.
    
- **ConsumedUnits:** Belirli bir lisans planındaki kullanıcılara atadığınız lisansların sayısı.
    
Tüm lisans planlarınızda kullanılabilen Microsoft 365 hizmetleriyle ilgili ayrıntıları görüntülemek için önce lisans planlarınızın listesini görüntüleyin.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Ardından lisans planları bilgilerini bir değişkende depolayın.

```powershell
$licenses = Get-AzureADSubscribedSku
```

Ardından hizmetleri belirli bir lisans planında görüntüleyin.

```powershell
$licenses[<index>].ServicePlans
```

\<index> , komutun görüntüsünden `Get-AzureADSubscribedSku | Select SkuPartNumber` lisans planının satır numarasını belirten bir tamsayıdır( eksi 1).

Örneğin, komutun `Get-AzureADSubscribedSku | Select SkuPartNumber` görüntüsü şuysa:

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

Ardından ENTERPRISEPREMIUM lisans planına yönelik hizmetleri görüntüleme komutu şu şekildedir:

```powershell
$licenses[2].ServicePlans
```

ENTERPRISEPREMIUM üçüncü satırdır. Bu nedenle, dizin değeri (3 - 1) veya 2'dir.

Lisans planlarının tam listesi (ürün adları olarak da bilinir), bunların dahil edilen hizmet planları ve bunlara karşılık gelen kolay adları için bkz. [Lisanslama için ürün adları ve hizmet planı tanımlayıcıları](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Windows PowerShell için Microsoft Azure Active Directory Modülünü kullanma

İlk olarak [Microsoft 365 kiracınıza bağlanın](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

>[!Note]
>Bu konuda açıklanan yordamları otomatik hale getiren bir PowerShell betiği mevcuttur. Özellikle betik, Sway dahil olmak üzere Microsoft 365 kuruluşunuzdaki hizmetleri görüntülemenize ve devre dışı bırakmanıza olanak tanır. Daha fazla bilgi için bkz. [PowerShell ile Sway erişimini devre dışı bırakma](disable-access-to-sway-with-microsoft-365-powershell.md).
>
    
Geçerli lisans planlarınız ve her bir plan için kullanılabilir lisanslar hakkındaki özet bilgileri görüntülemek için aşağıdaki komutu çalıştırın:
  
```powershell
Get-MsolAccountSku
```

>[!Note]
>PowerShell Core, Windows PowerShell modülü için Microsoft Azure Active Directory Modülünü ve adında **Msol** bulunan cmdlet'leri desteklemez. Bu cmdlet'leri kullanmaya devam etmek için bunları Windows PowerShell çalıştırmanız gerekir.
>

Sonuçlar aşağıdaki bilgileri içerir:
  
- **AccountSkuId:** söz dizimini `<CompanyName>:<LicensingPlan>`kullanarak kuruluşunuz için kullanılabilir lisans planlarını gösterin.  _\<CompanyName>_, Microsoft 365 kaydolduğunuz sırada sağladığınız değerdir ve kuruluşunuz için benzersizdir. Değer _\<LicensingPlan>_ herkes için aynıdır. Örneğin, değerinde `litwareinc:ENTERPRISEPACK`şirket adı `litwareinc`, lisans planı adı `ENTERPRISEPACK`ise Office 365 Kurumsal E3 için sistem adıdır.
    
- **ActiveUnits:** Belirli bir lisans planı için satın aldığınız lisansların sayısı.
    
- **WarningUnits:** Lisans planında yenilemediğiniz ve 30 günlük yetkisiz kullanım süresinden sonra sona erecek lisans sayısı.
    
- **ConsumedUnits:** Belirli bir lisans planındaki kullanıcılara atadığınız lisansların sayısı.
    
Tüm lisans planlarınızda kullanılabilen Microsoft 365 hizmetleriyle ilgili ayrıntıları görüntülemek için aşağıdaki komutu çalıştırın:
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

Aşağıdaki tabloda Microsoft 365 hizmet planları ve bunların en yaygın hizmetler için kolay adları gösterilmektedir. Hizmet planlarınızın listesi farklı olabilir. 
  
|**Hizmet planı**|**Açıklama**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Kurumlar için Microsoft 365 Uygulamaları *(eski adıyla Office 365 ProPlus)*  <br/> |
| `MCOSTANDARD` <br/> |Skype Kurumsal Çevrimiçi  <br/> |
| `SHAREPOINTWAC` <br/> |Office  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online Plan 2  <br/> |
   
Lisans planlarının tam listesi (ürün adları olarak da bilinir), bunların dahil edilen hizmet planları ve bunlara karşılık gelen kolay adları için bkz. [Lisanslama için ürün adları ve hizmet planı tanımlayıcıları](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

Belirli bir lisans planında kullanılabilen Microsoft 365 hizmetleriyle ilgili ayrıntıları görüntülemek için aşağıdaki söz dizimini kullanın.
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

Bu örnekte litwareinc:ENTERPRISEPACK (Office 365 Kurumsal E3) lisans planında bulunan hizmetler gösterilir.
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="see-also"></a>Ayrıca bkz.

[PowerShell ile Microsoft 365 kullanıcı hesaplarını, lisanslarını ve gruplarını yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[PowerShell ile Microsoft 365’i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Microsoft 365 için PowerShell'i kullanmaya başlama](getting-started-with-microsoft-365-powershell.md)