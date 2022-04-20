---
title: Kimlerin Microsoft 365 Grupları oluşturabileceğini yönetme
f1.keywords: NOCSH
ms.author: mikeplum
ms.reviewer: arvaradh
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- m365solution-collabgovernance
search.appverid:
- MET150
ms.assetid: 4c46c8cb-17d0-44b5-9776-005fced8e618
recommendations: false
description: Hangi kullanıcıların Microsoft 365 Grupları oluşturabileceğini denetlemeyi öğrenin.
ms.openlocfilehash: 992f5c62654f23f90f910f62dc3bb78199b949b0
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64946934"
---
# <a name="manage-who-can-create-microsoft-365-groups"></a>Kimlerin Microsoft 365 Grupları oluşturabileceğini yönetme

Varsayılan olarak, tüm kullanıcılar Microsoft 365 grupları oluşturabilir. Kullanıcıların BT'den yardım almadan işbirliği yapmaya başlamasını sağladığından bu önerilen yaklaşımdır.

İşletmeniz grup oluşturabilecek kullanıcıları kısıtlamanızı gerektiriyorsa, Microsoft 365 Grupları oluşturmayı belirli bir Microsoft 365 grubunun veya güvenlik grubunun üyeleriyle kısıtlayabilirsiniz.

Kullanıcıların iş standartlarınıza uygun olmayan ekipler veya gruplar oluşturmasından endişe duyuyorsanız, kullanıcıların bir eğitim kursunu tamamlayıp izin verilen kullanıcılar grubuna eklemesini zorunlu kılabilirsiniz.

Kimlerin grup oluşturabileceğini sınırladığınızda, bu, erişim için grupları kullanan tüm hizmetleri etkiler, örneğin:

- Outlook
- SharePoint
- Yammer
- Microsoft Teams
- Microsoft Stream
- Planner
- Power BI (klasik)
- Web için Project / Yol Haritası

Bu makaledeki adımlar, belirli rollerin üyelerinin Grup oluşturmasını engellemez. Microsoft 365 genel yöneticiler Microsoft 365 yönetim merkezi, Planner, Exchange ve SharePoint aracılığıyla grup oluşturabilir ancak Teams gibi diğer konumları oluşturamaz. Diğer roller, aşağıda listelenen sınırlı yollarla Microsoft 365 Grupları oluşturabilir.

- Exchange Yöneticisi: Exchange yönetim merkezi, Azure AD
- İş Ortağı Katmanı 1 Desteği: Microsoft 365 yönetim merkezi, Exchange yönetim merkezi, Azure AD
- İş Ortağı Katmanı 2 Desteği: Microsoft 365 yönetim merkezi, Exchange yönetim merkezi, Azure AD
- Dizin Yazarları: Azure AD
- SharePoint Yöneticisi: SharePoint yönetim merkezi, Azure AD
- Teams Hizmet Yöneticisi: Teams yönetim merkezi, Azure AD
- Kullanıcı Yöneticisi: Microsoft 365 yönetim merkezi, Azure AD

Bu rollerden birinin üyesiyseniz, kısıtlı kullanıcılar için Microsoft 365 Grupları oluşturabilir ve kullanıcıyı grubun sahibi olarak atayabilirsiniz.

## <a name="licensing-requirements"></a>Lisans gereksinimleri

Grupları kimin oluşturduğunu yönetmek için aşağıdaki kişilerin kendilerine atanmış Azure AD Premium lisansları veya Azure AD Temel EDU lisansları olmalıdır:

- Bu grup oluşturma ayarlarını yapılandıran yönetici
- Grup oluşturmasına izin verilen grup üyeleri

> [!NOTE]
> Azure lisanslarını atama hakkında daha fazla bilgi için [bkz. Azure Active Directory portalında lisans atama veya kaldırma](/azure/active-directory/fundamentals/license-users-groups).

Aşağıdaki kişilerin kendilerine atanmış Azure AD Premium veya Azure AD Temel EDU lisanslarına ihtiyacı yoktur:

- Microsoft 365 grupların üyesi olan ve başka gruplar oluşturma yeteneği olmayan kişiler.

## <a name="step-1-create-a-group-for-users-who-need-to-create-microsoft-365-groups"></a>1. Adım: Microsoft 365 grupları oluşturması gereken kullanıcılar için grup oluşturma

Kuruluşunuzdaki yalnızca bir grup, kimlerin Microsoft 365 Grupları oluşturabileceğini denetlemek için kullanılabilir. Ancak, diğer grupları bu grubun üyesi olarak iç içe yerleştirebilirsiniz.

Yukarıda listelenen rollerdeki yöneticilerin bu grubun üyesi olması gerekmez: grup oluşturma becerilerini korurlar.

1. Yönetim merkezinde [Gruplar sayfasına](https://admin.microsoft.com/adminportal/home#/groups) gidin.

2. **Grup Ekle'ye** tıklayın.

3. İstediğiniz grup türünü seçin. Grubun adını unutmayın! Daha sonra gerekecektir.

4. Grubu ayarlamayı bitirin, grup oluşturmak istediğiniz kişileri veya diğer grupları üye olarak ekleyin (sahip olarak değil).

Ayrıntılı yönergeler için bkz. [Microsoft 365 yönetim merkezi güvenlik grubu oluşturma, düzenleme veya silme](../admin/email/create-edit-or-delete-a-security-group.md).

## <a name="step-2-run-powershell-commands"></a>2. Adım: PowerShell komutlarını çalıştırma

Grup düzeyinde konuk erişimi ayarını değiştirmek [için Azure Active Directory PowerShell'in Graph (AzureAD) (](/powershell/azure/active-directory/install-adv2)modül adı **AzureADPreview**) önizleme sürümünü kullanmanız gerekir:

- Azure AD PowerShell modülünün herhangi bir sürümünü daha önce yüklemediyseniz bkz [. Azure AD Modülünü Yükleme](/powershell/azure/active-directory/install-adv2?preserve-view=true&view=azureadps-2.0-preview) ve genel önizleme sürümünü yükleme yönergelerini izleyin.

- Azure AD PowerShell modülünün (AzureAD) 2.0 genel kullanılabilirlik sürümü yüklüyse, PowerShell oturumunuzda çalıştırarak `Uninstall-Module AzureAD` kaldırmanız ve ardından çalıştırarak `Install-Module AzureADPreview`önizleme sürümünü yüklemeniz gerekir.

- Önizleme sürümünü zaten yüklediyseniz, bu modülün en son sürümü olduğundan emin olmak için komutunu çalıştırın `Install-Module AzureADPreview` .

Aşağıdaki betiği Not Defteri veya [Windows PowerShell ISE](/powershell/scripting/components/ise/introducing-the-windows-powershell-ise) gibi bir metin düzenleyicisine kopyalayın.

değerini, oluşturduğunuz grubun adıyla değiştirin *\<GroupName\>* . Örneğin:

`$GroupName = "Group Creators"`

Dosyayı GroupCreators.ps1 olarak kaydedin.

PowerShell penceresinde, dosyayı kaydettiğiniz konuma gidin ("CD \<FileLocation\>") yazın.

Şu komutu yazarak betiği çalıştırın:

`.\GroupCreators.ps1`

ve istendiğinde [yönetici hesabınızla oturum açın](../enterprise/connect-to-microsoft-365-powershell.md#step-2-connect-to-azure-ad-for-your-microsoft-365-subscription) .

```PowerShell
$GroupName = "<GroupName>"
$AllowGroupCreation = $False

Connect-AzureAD

$settingsObjectID = (Get-AzureADDirectorySetting | Where-object -Property Displayname -Value "Group.Unified" -EQ).id
if(!$settingsObjectID)
{
    $template = Get-AzureADDirectorySettingTemplate | Where-object {$_.displayname -eq "group.unified"}
    $settingsCopy = $template.CreateDirectorySetting()
    New-AzureADDirectorySetting -DirectorySetting $settingsCopy
    $settingsObjectID = (Get-AzureADDirectorySetting | Where-object -Property Displayname -Value "Group.Unified" -EQ).id
}

$settingsCopy = Get-AzureADDirectorySetting -Id $settingsObjectID
$settingsCopy["EnableGroupCreation"] = $AllowGroupCreation

if($GroupName)
{
  $settingsCopy["GroupCreationAllowedGroupId"] = (Get-AzureADGroup -SearchString $GroupName).objectid
} else {
$settingsCopy["GroupCreationAllowedGroupId"] = $GroupName
}
Set-AzureADDirectorySetting -Id $settingsObjectID -DirectorySetting $settingsCopy

(Get-AzureADDirectorySetting -Id $settingsObjectID).Values
```

Betiğin son satırında güncelleştirilmiş ayarlar görüntülenir:

![PowerShell betik çıkışının ekran görüntüsü.](../media/952cd982-5139-4080-9add-24bafca0830c.png)

Gelecekte hangi grubun kullanılacağını değiştirmek istiyorsanız, betiği yeni grubun adıyla yeniden çalıştırabilirsiniz.

Grup oluşturma kısıtlamasını kapatmak ve tüm kullanıcıların grup oluşturmasına yeniden izin vermek istiyorsanız, $GroupName "" olarak ayarlayın ve $AllowGroupCreation "True" olarak ayarlayın ve betiği yeniden çalıştırın.

## <a name="step-3-verify-that-it-works"></a>3. Adım: Çalıştığını doğrulama

Değişikliklerin geçerlilik kazanması otuz dakika veya daha fazla sürebilir. Aşağıdakileri yaparak yeni ayarları doğrulayabilirsiniz:

1. Grup oluşturma becerisine sahip olmaması gereken birinin kullanıcı hesabıyla Microsoft 365 oturum açın. Diğer bir ifadeyle, oluşturduğunuz grubun veya yöneticinin üyesi değildir.

2. **Planner** kutucuğunu seçin.

3. Planner'da, sol gezinti **bölmesinden Yeni Plan'ı** seçerek bir plan oluşturun.

4. Plan ve grup oluşturmanın devre dışı bırakıldığını belirten bir ileti almalısınız.

Grubun bir üyesiyle aynı yordamı yeniden deneyin.

> [!NOTE]
> Grubun üyeleri grup oluşturamıyorsa, [OWA posta kutusu ilkeleri](/powershell/module/exchange/set-owamailboxpolicy) aracılığıyla engellenmediklerinden emin olun.

## <a name="related-topics"></a>İlgili konular

[İşbirliği idaresi planlama önerileri](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[İşbirliği idare planınızı oluşturma](collaboration-governance-first.md)

[Office 365 PowerShell ile çalışmaya başlama](../enterprise/getting-started-with-microsoft-365-powershell.md)

[Azure Active Directory'de self servis grup yönetimini ayarlama](/azure/active-directory/users-groups-roles/groups-self-service-management)

[Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy)

[Grup ayarlarını yapılandırmak için cmdlet'leri Azure Active Directory](/azure/active-directory/users-groups-roles/groups-settings-cmdlets)
