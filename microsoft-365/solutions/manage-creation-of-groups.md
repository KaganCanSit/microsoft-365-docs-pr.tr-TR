---
title: Gruplarda kimlerin oluştur Microsoft 365 yönetme
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
description: Grup oluşturmak için hangi kullanıcıların oluşturula Microsoft 365 öğrenin.
ms.openlocfilehash: 4280b6859358580547302ccf9497e8cd1e7ed752
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63032505"
---
# <a name="manage-who-can-create-microsoft-365-groups"></a>Gruplarda kimlerin oluştur Microsoft 365 yönetme

Varsayılan olarak, tüm kullanıcılar grup Microsoft 365 oluşturabilir. Önerilen yaklaşım bu seçenektir, çünkü kullanıcıların IT'den yardım almadan işbirliğine başlamasına olanak sağlar.

İşletmeniz, kimlerin grup oluştur azını kısıtla sınırlamanızı gerektiriyorsa, Microsoft 365 grupları oluşturmanızı belirli bir grup veya Microsoft 365 grubu üyeleriyle kısıtlayan bir sınırlama kullanabilirsiniz.

İş standartlarına uymayan ekipler veya gruplar oluşturma konusunda endişeleriniz varsa, kullanıcıların bir eğitim kursu tamamlamalarını ve sonra da bunları izin verilen kullanıcı grubuna eklemelerini gerektirmeyi düşünebilirsiniz.

Kimlerin grup oluştur etkileyeceğini sınırlarken, erişim için gruplara güvenen tüm hizmetleri etkiler. Bu, aşağıdakiler de dahil:

- Outlook
- SharePoint
- Yammer
- Microsoft Teams
- Microsoft Stream
- Planner
- Power BI (klasik)
- Project sayfası / Yol Haritası

Bu makaledeki adımlar, belirli rollerin üyelerinin Gruplar oluşturmasını engellemez. Office 365 yöneticiler Çevrimiçi Gruplar, Microsoft 365 yönetim merkezi, Planner, Exchange ve SharePoint aracılığıyla Gruplar oluşturabilir. Diğer roller aşağıda listelenen sınırlı bir şekilde Gruplar oluşturabilir.

- Exchange Yönetici: Exchange merkezi, Azure AD
- İş Ortağı Katman 1 Desteği: Microsoft 365 yönetim merkezi, Exchange merkezi, Azure AD
- İş Ortağı Katman 2 Desteği: Microsoft 365 yönetim merkezi, Exchange merkezi, Azure AD
- Dizin Yazarları: Azure AD
- SharePoint Yönetici: SharePoint merkezi, Azure AD
- Teams Yöneticisi: Teams merkezi, Azure AD
- Kullanıcı Yöneticisi: Microsoft 365 yönetim merkezi, Azure AD

Bu rollerden birinin üyesiyseniz, kısıtlanmış kullanıcılar için Microsoft 365 Grupları oluşturabilir ve sonra da kullanıcıya grubun sahibi olarak atabilirsiniz.

## <a name="licensing-requirements"></a>Lisans gereksinimleri

Kimlerin grup oluşturduğunı yönetmek için, aşağıdaki kişilerin Azure AD Premium lisans ataması gerekir:

- Bu grup oluşturma ayarlarını yapılandıran yönetici
- Grup oluşturmasına izin verilen grubun üyeleri

> [!NOTE]
> Azure [lisansları atama hakkında daha fazla Azure Active Directory için](/azure/active-directory/fundamentals/license-users-groups) bkz. Kullanıcı portalında lisans atama veya kaldırma.

Aşağıdaki kişilerin bu lisansların Azure AD Premium ihtiyacı vardır:

- Grup veya grup Microsoft 365 olan ve başka gruplar oluşturma becerisine sahip kişiler.

## <a name="step-1-create-a-group-for-users-who-need-to-create-microsoft-365-groups"></a>1. Adım: Grup oluşturması gereken kullanıcılar için Microsoft 365 oluşturma

Kimlerin Grup oluşturabileceklerini kontrol etmek için, yalnızca bir grup kullanılabilir. Ancak, diğer grupları bu grubun üyeleri olarak iç içe yerleştirmeyi de slarının.

Yukarıda listelenen rollerde yer alan yöneticilerin bu gruba üye olması gerek değildir: grup oluşturma becerisini korurlar.

1. Yönetim merkezinde Gruplar sayfasına [gidin](https://admin.microsoft.com/adminportal/home#/groups).

2. Grup **Ekle'ye tıklayın**.

3. Istediğiniz grup türünü seçin. Grubun adını unutmayın! Daha sonra gerekecektir.

4. Grubu ayarlamayı bitirip, kendi kuruluş içinde grup oluşturabilecek diğer grupları ve diğer grupları eklemeyi bitirin.

Ayrıntılı yönergeler için bkz[. Grupta güvenlik grubu oluşturma, düzenleme veya Microsoft 365 yönetim merkezi](../admin/email/create-edit-or-delete-a-security-group.md).

## <a name="step-2-run-powershell-commands"></a>2. Adım: PowerShell komutlarını çalıştırma

Grup düzeyi konuk erişimi ayarını [değiştirmek için Azure Active Directory PowerShell Graph (AzureAD) (AzureAD) (](/powershell/azure/active-directory/install-adv2)**modül adı AzureADPreview**) önizleme sürümünü kullansanız gerekir:

- Daha önce Azure AD PowerShell modülünün herhangi bir sürümünü yüklemedıysanız, [Bkz. Azure AD](/powershell/azure/active-directory/install-adv2?preserve-view=true&view=azureadps-2.0-preview) Modülü'ne yükleme ve genel önizleme sürümünü yükleme yönergelerini izleyin.

- Azure AD PowerShell modülünün (AzureAD) 2.0 genel kullanılabilirlik sürümü yüklüyse, `Uninstall-Module AzureAD` PowerShell oturumda çalıştırarak bu modülü kaldırmanız ve sonra önizleme sürümünü çalıştırarak yüklemeniz gerekir `Install-Module AzureADPreview`.

- Önizleme sürümünü zaten yüklemişsanız, bu modülün `Install-Module AzureADPreview` en son sürümü olduğundan emin olmak için çalıştırın.

Aşağıdaki betiği ISE veya NOT DEFTERI gibi bir metin [düzenleyicisine Windows PowerShell.](/powershell/scripting/components/ise/introducing-the-windows-powershell-ise)

Oluşturduğunuz *\<GroupName\>* grubun adıyla değiştirin. Örneğin:

`$GroupName = "Group Creators"`

Dosyayı farklı bir GroupCreators.ps1.

PowerShell penceresinde, dosyayı kayıtlı konuma gidin ("CD" yazın \<FileLocation\>).

Betiği çalıştırmak için şunları yazın:

`.\GroupCreators.ps1`

ve [istendiğinde yönetici hesabınızla](../enterprise/connect-to-microsoft-365-powershell.md#step-2-connect-to-azure-ad-for-your-microsoft-365-subscription) oturum açın.

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

Betiğin son satırı güncelleştirilmiş ayarları görüntüler:

![PowerShell betik çıkışını ekran görüntüsü.](../media/952cd982-5139-4080-9add-24bafca0830c.png)

Gelecekte hangi grubun kullanıı değiştirecekse, betiği yeni grubun adıyla yeniden çalıştıracaksanız.

Grup oluşturma kısıtlamalarını kapatmak ve yeniden tüm kullanıcıların grup oluşturmasına izin vermek için, $GroupName", "True" olarak ayarlayın $AllowGroupCreation doğru olarak ayarlayın ve betiği yeniden çalıştırabilirsiniz.

## <a name="step-3-verify-that-it-works"></a>3. Adım: Çalıştığını doğrulama

Değişikliklerin etkili hale etkileri otuz dakika veya daha uzun sürebilir. Yeni ayarları doğrulamak için şunları yapabilirsiniz:

1. Grup oluşturma Microsoft 365 sahip olması gereken birinin kullanıcı hesabıyla oturum açın. Başka bir ifadeyle, oluşturduğunuz grubun üyesi veya yöneticisi değildir.

2. **Planner kutucuğunu** seçin.

3. Planner'da, **sol gezinti bölmesinde** Yeni Plan'ı seçerek bir plan oluşturun.

4. Plan ve grup oluşturmanın devre dışı bırakılmıştır iletisi alırsınız.

Aynı yordamı grubun bir üyesiyle birlikte yeniden deneyin.

> [!NOTE]
> Grubun üyeleri grup oluşturamazsa, OWA posta kutusu ilkesi aracılığıyla engellenmiş [olup olmadığını kontrol edin](/powershell/module/exchange/set-owamailboxpolicy).

## <a name="related-topics"></a>İlgili konular

[İşbirliği yönetim planlaması önerileri](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[İşbirliği yönetim planınızı oluşturma](collaboration-governance-first.md)

[Office 365 PowerShell ile çalışmaya başlama](../enterprise/getting-started-with-microsoft-365-powershell.md)

[Grup içinde self servis grup Azure Active Directory](/azure/active-directory/users-groups-roles/groups-self-service-management)

[Set-ExecutionPolicy](/powershell/module/microsoft.powershell.security/set-executionpolicy)

[Azure Active Directory ayarlarını yapılandırmak için cmdlet'leri yapılandırma](/azure/active-directory/users-groups-roles/groups-settings-cmdlets)
