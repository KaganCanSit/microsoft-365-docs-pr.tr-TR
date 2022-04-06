---
title: Konukların belirli bir gruba eklenmesini önleme
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
description: Konukların belirli bir gruba eklenmesini engellemeyi öğrenin
ms.openlocfilehash: 4b9ebc6366934db52c30d51091ac9991ff82d8c3
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2022
ms.locfileid: "64570073"
---
# <a name="prevent-guests-from-being-added-to-a-specific-microsoft-365-group-or-microsoft-teams-team"></a>Konukların belirli bir ekip üyesine veya bir Microsoft 365 grubuna Microsoft Teams engelleme

Çoğu grup ve ekipte konuk erişimine izin vermek, ancak bazı durumlarda konuk erişimini engellemek istiyorsanız, tek tek gruplarda ve ekiplerde konuk erişimini engelleyebilirsiniz. (Bir ekipte konuk erişimini engellemek, ilişkili gruba konuk erişimini engelleyerek yapılır.) Bu, yeni konukların eklenmesini önler, ancak zaten grupta veya ekipte yer alan konukları kaldırmaz.

Kuruluşta duyarlılık etiketleri kullanıyorsanız, konuk erişimini grup temelinde kontrol etmek için bu etiketleri kullanmanızı öneririz. Bunun nasıl olduğu hakkında bilgi için, sitelerine, gruplara ve [sitelere Microsoft Teams için Microsoft 365 duyarlılık SharePoint kullanın](../compliance/sensitivity-labels-teams-groups-sites.md). Önerilen yaklaşım bu.

## <a name="change-group-settings-using-microsoft-powershell"></a>Microsoft PowerShell kullanarak grup ayarlarını değiştirme

Ayrıca, PowerShell kullanarak yeni konukların tek tek gruplara eksini önabilirsiniz. (Ekibin ilişkili web sitesinde ayrı SharePoint denetimleri [olduğunu unutmayın](/sharepoint/change-external-sharing-site).)

Grup düzeyi konuk erişimi ayarını [değiştirmek Azure Active Directory PowerShell Graph](/powershell/azure/active-directory/install-adv2) (**modül adı AzureADPreview**) önizleme sürümünü kullansanız gerekir:

- Daha önce Azure AD PowerShell modülünün herhangi bir sürümünü yüklemedıysanız, [Bkz. Azure AD](/powershell/azure/active-directory/install-adv2?preserve-view=true&view=azureadps-2.0-preview) Modülü'ne yükleme ve genel önizleme sürümünü yükleme yönergelerini izleyin.

- Azure AD PowerShell modülünün (AzureAD) 2.0 genel kullanılabilirlik sürümü yüklüyse, `Uninstall-Module AzureAD` PowerShell oturumda çalıştırarak bu modülü kaldırmanız ve sonra önizleme sürümünü çalıştırarak yüklemeniz gerekir `Install-Module AzureADPreview`.

- Önizleme sürümünü zaten yüklemişsanız, bu modülün `Install-Module AzureADPreview` en son sürümü olduğundan emin olmak için çalıştırın.

> [!NOTE]
> Bu komutları çalıştırmak için genel yönetici haklarına sahip olmak gerekir. 

Konuk erişimini engellemek istediğiniz *\<GroupName\>* grubun adını değiştirerek aşağıdaki betiği çalıştırın.

```PowerShell
$GroupName = "<GroupName>"

Connect-AzureAD

$template = Get-AzureADDirectorySettingTemplate | ? {$_.displayname -eq "group.unified.guest"}
$settingsCopy = $template.CreateDirectorySetting()
$settingsCopy["AllowToAddGuests"]=$False
$groupID= (Get-AzureADGroup -SearchString $GroupName).ObjectId
New-AzureADObjectSetting -TargetType Groups -TargetObjectId $groupID -DirectorySetting $settingsCopy
```

Ayarlarınızı doğrulamak için bu komutu çalıştırın:

```PowerShell
Get-AzureADObjectSetting -TargetObjectId $groupID -TargetType Groups | fl Values
```

Doğrulama şöyle görünüyor:
    
![Konuk grubu erişiminin yanlış olarak ayar olduğunu gösteren PowerShell penceresinin ekran görüntüsü.](../media/09ebfb4f-859f-44c3-a29e-63a59fd6ef87.png)

Konukların belirli bir gruba erişimine izin vermek için bu ayarı yeniden değiştirmek isterseniz, ```<GroupName>``` konuk erişimine izin vermek istediğiniz grubun adını değiştirerek aşağıdaki betiği çalıştırın.

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

## <a name="allow-or-block-guest-access-based-on-their-domain"></a>Konuk kullanıcıların etki alanına göre erişime izin verme veya erişimini engelleme

Belirli bir etki alanını kullanan konuklara izin ve engelleyebilirsiniz. Örneğin, işletmeniz (Contoso) ile başka bir işletme (Fabrikam) arasında bir ortaklık varsa, fabrikam'a izin vermek için kullanıcılarınız bu işletmeden konukları gruplarına ekleyebilir.

Daha fazla bilgi için bkz [. Belirli kuruluşlardan B2B kullanıcılarına davetlere izin verme veya davetleri engelleme](/azure/active-directory/b2b/allow-deny-list).

## <a name="add-guests-to-the-global-address-list"></a>Genel adres listesine konuk ekleme

Varsayılan olarak konuklar Genel Adres Listesi'Exchange görünmez. Bir konuğun genel adres listesinde görünür olması için aşağıda listelenen adımları kullanın.

Aşağıdakini çalıştırarak konuğun ObjectID'lerini bulun:

```PowerShell
Get-AzureADUser -Filter "userType eq 'Guest'"
```

Ardından ObjectID, GivenName, Surname, DisplayName ve TelephoneNumber için uygun değerleri kullanarak aşağıdakini çalıştırın.

```PowerShell
Set-AzureADUser -ObjectId cfcbd1a0-ed18-4210-9b9d-cf0ba93cf6b2 -ShowInAddressList $true -GivenName 'Megan' -Surname 'Bowen' -DisplayName 'Megan Bowen' -TelephoneNumber '555-555-5555'
```

## <a name="related-topics"></a>İlgili konular

[İşbirliği yönetim planlaması önerileri](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[İşbirliği yönetim planınızı oluşturma](collaboration-governance-first.md)

[Grupta Grup üyeliğini Microsoft 365 yönetim merkezi](../admin/create-groups/add-or-remove-members-from-groups.md)
  
[Azure Active Directory incelemeleri](/azure/active-directory/active-directory-azure-ad-controls-perform-access-review)

[Set-AzureADUser](/powershell/module/azuread/set-azureaduser)
