---
title: PowerShell Microsoft 365 ve hizmetleri görüntüleme
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: PowerShell'in, Microsoft 365 kurumda bulunan lisans planları, hizmetleri ve lisanslar hakkında bilgileri görüntüleme Microsoft 365 açıklar.
ms.openlocfilehash: 3b90596c68e3beadcc2b33ef59ff9c3503b84f8a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986689"
---
# <a name="view-microsoft-365-licenses-and-services-with-powershell"></a>PowerShell Microsoft 365 ve hizmetleri görüntüleme

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Her Microsoft 365 aboneliği aşağıdaki öğelerden oluşur:

- **Lisans planları** Bunlara lisans planları veya proje planları Microsoft 365 bilinir. Lisans planları, Microsoft 365 kullanılabilen lisans hizmetlerini tanımlar. Microsoft 365 aboneliğiniz birden çok lisans planı içerebilir. Örnek bir lisans planı Microsoft 365 E3.
    
- **Hizmetler** Bunlar, hizmet planları olarak da bilinir. Hizmetler, Microsoft 365 planlarında (daha önce Exchange Online ve Kurumlar için Microsoft 365 Uygulamaları) gibi her lisans planında kullanılabilen Exchange Online, özellikler ve Office 365 ProPlus. Kullanıcıların, farklı hizmetlere erişim veren farklı lisans planlarından onlara atanmış birden çok lisansı olabilir.
    
- **Lisanslar** Her lisans planı, satın aldığınız lisans sayısını içerir. Lisans planı tarafından tanımlanan yeni hizmetleri Microsoft 365 için kullanıcılara lisans atarsiniz. Her kullanıcı hesabının lisans hizmetlerinden biri ile oturum açlarını ve hizmetleri kullanmalarını için en az Microsoft 365 lisansa ihtiyacı vardır.
    
Microsoft 365 Microsoft 365 da bulunan lisans planları, lisanslar ve hizmetlerle ilgili ayrıntıları görüntülemek için Microsoft 365 kullanabilirsiniz. Farklı aboneliklerde bulunan ürünler, özellikler ve hizmetler hakkında daha fazla bilgi Office 365 Plan [Seçenekleri'Office 365 bakın](/office365/servicedescriptions/office-365-platform-service-description/office-365-plan-options).


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Graph modülü için Azure Active Directory PowerShell'i kullanma

İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Geçerli lisans planlarınız ve her plan için kullanılabilir lisanslar hakkında özet bilgileri görüntülemek için şu komutu çalıştırın:
  
```powershell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

Sonuçlar şunları içerir:
  
- **SkuPartNumber:** Kurum için kullanılabilir lisans planlarını gösterir. Örneğin, `ENTERPRISEPACK` E3'ler için lisans Office 365 Kurumsal adıdır.
    
- **Etkin:** Belirli bir lisans planı için satın aldığınız lisans sayısı.
    
- **ConsumedUnits:** Belirli bir lisans planından kullanıcılara atadığı lisans sayısı.
    
Tüm lisans planlarında Microsoft 365 hizmetleriyle ilgili ayrıntıları görüntülemek için, önce lisans planlarının listesini görüntüleme.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Ardından, lisans planı bilgilerini bir değişkende depolanın.

```powershell
$licenses = Get-AzureADSubscribedSku
```

Ardından, hizmetleri belirli bir lisans planında görüntüleme.

```powershell
$licenses[<index>].ServicePlans
```

\<index> , komutun görüntüsünden eksi 1'e kadar olan lisans planının satır `Get-AzureADSubscribedSku | Select SkuPartNumber` numarasını belirten bir tamsayıdır.

Örneğin, komutun görüntüsü `Get-AzureADSubscribedSku | Select SkuPartNumber` aşağıdaki gibi ise:

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

Ardından ENTERPRISEPREMIUM lisans planının hizmetlerini görüntüleme komutu şu şekildedir:

```powershell
$licenses[2].ServicePlans
```

ENTERPRISEPREMIUM üçüncü satırdır. Bu nedenle, dizin değeri (3 - 1) veya 2 olur.

Lisans planlarının (ürün adları olarak da bilinir), dahil edilen hizmet planlarının ve bunların uygun adlarının tam listesi için bkz. Lisans için ürün adları ve [hizmet planı tanımlayıcıları](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Kaynak için Microsoft Azure Active Directory Modülü'Windows PowerShell

İlk olarak[, kiracınıza bağlan Microsoft 365 bağlanin](connect-to-microsoft-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

>[!Note]
>Bu konuda açıklanan yordamları otomatik haleleştiren bir PowerShell betiği kullanılabilir. Özel olarak betik, Sway dahil olmak üzere Microsoft 365 hizmetleri görüntülemenize ve devre dışı bırakmanıza olanak sağlar. Daha fazla bilgi için bkz. [PowerShell ile Sway'e erişimi devre dışı bırakma](disable-access-to-sway-with-microsoft-365-powershell.md).
>
    
Geçerli lisans planlarınız ve her planın kullanılabilir lisansları hakkında özet bilgileri görüntülemek için aşağıdaki komutu çalıştırın:
  
```powershell
Get-MsolAccountSku
```

>[!Note]
>PowerShell Core, **Msol'Microsoft Azure Active Directory Msol** Windows PowerShell cmdlet'leri için Modül Adını Desteklemez. Bu cmdlet'leri kullanmaya devam etmek için, tüm cmdlet'leri Windows PowerShell.
>

Sonuçlar aşağıdaki bilgileri içerir:
  
- **AccountSkuId:** Söz dizimini kullanarak, organizasyon için kullanılabilir lisans planlarını gösterebilirsiniz `<CompanyName>:<LicensingPlan>`.  _\<CompanyName>_ Microsoft 365'a kaydolarak Microsoft 365, sizin için benzersiz olan değerdir. Değer _\<LicensingPlan>_ herkes için aynıdır. Örneğin, değerinde şirketin `litwareinc`adı `litwareinc:ENTERPRISEPACK`, lisans planı `ENTERPRISEPACK`adı da E3 için sistem adı Office 365 Kurumsal.
    
- **ActiveUnits:** Belirli bir lisans planı için satın aldığınız lisans sayısı.
    
- **UyarıUnits:** Lisans planında yenilememişsiniz ve 30 günlük yetkisiz kullanım süresinin ardından süresi dolacak lisans sayısı.
    
- **ConsumedUnits:** Belirli bir lisans planından kullanıcılara atadığı lisans sayısı.
    
Tüm lisans planlarında Microsoft 365 hizmetleriyle ilgili ayrıntıları görüntülemek için aşağıdaki komutu çalıştırın:
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

Aşağıdaki tabloda, en yaygın Microsoft 365 planları ve kolay adları yer alır. Hizmet planları listeniz farklı olabilir. 
  
|**Hizmet planı**|**Açıklama**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Hak Yönetimi (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Kurumlar için Microsoft 365 Uygulamaları *(daha önce adlandırılmış Office 365 ProPlus)*  <br/> |
| `MCOSTANDARD` <br/> |Skype Kurumsal Çevrimiçi  <br/> |
| `SHAREPOINTWAC` <br/> |Office  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Exchange Online Plan 2  <br/> |
   
Lisans planlarının (ürün adları olarak da bilinir), dahil edilen hizmet planlarının ve bunların uygun adlarının tam listesi için bkz. Lisans için ürün adları ve [hizmet planı tanımlayıcıları](/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

Belirli bir lisans planında Microsoft 365 hizmetleriyle ilgili ayrıntıları görüntülemek için aşağıdaki söz dizimi kullanın.
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

Bu örnek, litwareinc:ENTERPRISEPACK (Office 365 Kurumsal E3) lisans planında bulunan hizmetleri gösterir.
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="see-also"></a>Ayrıca bkz.

[PowerShell Microsoft 365 hesaplarını, lisanslarını ve gruplarını yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
  
[PowerShell Microsoft 365'i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Microsoft 365 için PowerShell ile çalışmaya Microsoft 365](getting-started-with-microsoft-365-powershell.md)