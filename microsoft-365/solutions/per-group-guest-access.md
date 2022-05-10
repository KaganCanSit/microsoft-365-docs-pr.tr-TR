---
title: Konukların belirli bir gruba eklenmesini engelleme
ms.reviewer: arvaradh
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
recommendations: false
description: Konukların belirli bir gruba eklenmesini nasıl önleyeceğinizi öğrenin
ms.openlocfilehash: f050011427ceeeff8347c2acd5b6d3fbbcf11bec
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/09/2022
ms.locfileid: "65285324"
---
# <a name="prevent-guests-from-being-added-to-a-specific-microsoft-365-group-or-microsoft-teams-team"></a>Konukların belirli bir Microsoft 365 grubuna veya Microsoft Teams ekibine eklenmesini engelleme

Çoğu gruba ve takıma konuk erişimine izin vermek istiyorsanız ancak konuk erişimini engellemek istediğiniz bir yere sahipseniz, tek tek gruplar ve ekipler için konuk erişimini engelleyebilirsiniz. (Takıma konuk erişimini engelleme işlemi, ilişkili gruba konuk erişimini engelleyerek yapılır.) Bu, yeni konukların eklenmesini engeller ancak zaten grupta veya ekipte olan konukları kaldırmaz.

Kuruluşunuzda duyarlılık etiketleri kullanıyorsanız, grup başına konuk erişimini denetlemek için bunları kullanmanızı öneririz. Bunun nasıl yapılacağını öğrenmek için Microsoft Teams[, Microsoft 365 grupları ve SharePoint sitelerindeki içeriği korumak için duyarlılık etiketlerini kullanın](../compliance/sensitivity-labels-teams-groups-sites.md). Önerilen yaklaşım budur.

## <a name="change-group-settings-using-microsoft-powershell"></a>Microsoft PowerShell kullanarak grup ayarlarını değiştirme

Ayrıca PowerShell'i kullanarak tek tek gruplara yeni konuklar eklenmesini engelleyebilirsiniz. (Ekibin ilişkili SharePoint sitesinde [ayrı konuk paylaşım denetimleri](/sharepoint/change-external-sharing-site) olduğunu unutmayın.)

Grup düzeyinde konuk erişimi ayarını değiştirmek [için Graph için Azure Active Directory PowerShell'in](/powershell/azure/active-directory/install-adv2) önizleme sürümünü (modül adı **AzureADPreview**) kullanmanız gerekir:

- Azure AD PowerShell modülünün herhangi bir sürümünü daha önce yüklemediyseniz bkz[. Azure AD Modülünü Yükleme](/powershell/azure/active-directory/install-adv2?preserve-view=true&view=azureadps-2.0-preview) ve genel önizleme sürümünü yüklemek için yönergeleri izleyin.

- Azure AD PowerShell modülünün (AzureAD) 2.0 genel kullanılabilirlik sürümü yüklüyse, PowerShell oturumunuzda çalıştırarak `Uninstall-Module AzureAD` kaldırmanız ve ardından çalıştırarak `Install-Module AzureADPreview`önizleme sürümünü yüklemeniz gerekir.

- Önizleme sürümünü zaten yüklediyseniz, bu modülün en son sürümü olduğundan emin olmak için komutunu çalıştırın `Install-Module AzureADPreview` .

> [!NOTE]
> Bu komutları çalıştırmak için genel yönetici haklarına sahip olmanız gerekir. 

Konuk erişimini engellemek istediğiniz grubun adına değiştirerek *\<GroupName\>* aşağıdaki betiği çalıştırın.

```PowerShell
$GroupName = "<GroupName>"

Connect-AzureAD

$template = Get-AzureADDirectorySettingTemplate | ? {$_.displayname -eq "group.unified.guest"}
$settingsCopy = $template.CreateDirectorySetting()
$settingsCopy["AllowToAddGuests"]=$False
$groupID= (Get-AzureADGroup -SearchString $GroupName).ObjectId
New-AzureADObjectSetting -TargetType Groups -TargetObjectId $groupID -DirectorySetting $settingsCopy
```

Ayarlarınızı doğrulamak için şu komutu çalıştırın:

```PowerShell
Get-AzureADObjectSetting -TargetObjectId $groupID -TargetType Groups | fl Values
```

Doğrulama şu şekilde görünür:
    
![Konuk grup erişiminin false olarak ayarlandığını gösteren PowerShell penceresinin ekran görüntüsü.](../media/09ebfb4f-859f-44c3-a29e-63a59fd6ef87.png)

Belirli bir gruba konuk erişimine izin vermek için ayarı yeniden değiştirmek isterseniz, aşağıdaki betiği çalıştırarak konuk erişimine izin vermek istediğiniz grubun adına geçin ```<GroupName>``` .

```PowerShell
$GroupName = "<GroupName>"

Connect-AzureAD

$template = Get-AzureADDirectorySettingTemplate | ? {$_.displayname -eq "group.unified.guest"}
$settingsCopy = $template.CreateDirectorySetting()
$settingsCopy["AllowToAddGuests"]=$True
$groupID= (Get-AzureADGroup -SearchString $GroupName).ObjectId
$id = (get-AzureADObjectSetting -TargetType groups -TargetObjectId $groupID).id
Set-AzureADObjectSetting -TargetType Groups -TargetObjectId $groupID -DirectorySetting $settingsCopy -id $id
```

## <a name="allow-or-block-guest-access-based-on-their-domain"></a>Etki alanına göre konuk erişimine izin verme veya erişimi engelleme

Belirli bir etki alanı kullanan konuklara izin verebilir veya bunları engelleyebilirsiniz. Örneğin, işletmenizin (Contoso) başka bir işletmeyle (Fabrikam) ortaklığı varsa, kullanıcılarınızın bu konukları gruplarına ekleyebilmesi için fabrikam'ı izin verilenler listenize ekleyebilirsiniz.

Daha fazla bilgi için bkz. [Belirli kuruluşların B2B kullanıcılarına yönelik davetlere izin verme veya davetleri engelleme](/azure/active-directory/b2b/allow-deny-list).

## <a name="add-guests-to-the-global-address-list"></a>Genel adres listesine konuk ekleme

Varsayılan olarak, konuklar Exchange Genel Adres Listesi'nde görünmez. Bir konuğun genel adres listesinde görünür olmasını sağlamak için aşağıda listelenen adımları kullanın.

Çalıştırarak konuğun ObjectID değerini bulun:

```PowerShell
get-AzureADUser -all $true | ?{$_.CreationType -eq "Invitation"}
```

Ardından ObjectID, GivenName, Soyad, DisplayName ve TelephoneNumber için uygun değerleri kullanarak aşağıdakileri çalıştırın.

```PowerShell
Set-AzureADUser -ObjectId cfcbd1a0-ed18-4210-9b9d-cf0ba93cf6b2 -ShowInAddressList $true -GivenName 'Megan' -Surname 'Bowen' -DisplayName 'Megan Bowen' -TelephoneNumber '555-555-5555'
```

## <a name="related-topics"></a>İlgili konular

[İşbirliği idaresi planlama önerileri](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[İşbirliği idare planınızı oluşturma](collaboration-governance-first.md)

[Microsoft 365 yönetim merkezi Grup üyeliğini yönetme](../admin/create-groups/add-or-remove-members-from-groups.md)
  
[erişim gözden geçirmelerini Azure Active Directory](/azure/active-directory/active-directory-azure-ad-controls-perform-access-review)

[Set-AzureADUser](/powershell/module/azuread/set-azureaduser)
