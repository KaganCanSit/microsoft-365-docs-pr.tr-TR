---
title: PowerShell Microsoft 365 Grupları Yönetme
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
- admindeeplinkMAC
- admindeeplinkEXCHANGE
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: Bu makalede, PowerShell'de grup üyelerine ve gruplara Microsoft 365 görevlerin nasıl yerine kullanıldığı hakkında bilgi bulabilirsiniz.
ms.openlocfilehash: 460444e1cb2f862f4d96ed6aad0178a146864658
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019502"
---
# <a name="manage-microsoft-365-groups-with-powershell"></a>PowerShell Microsoft 365 Grupları Yönetme

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Bu makalede, Microsoft PowerShell'de Gruplar için ortak yönetim görevleri gerçekleştirme adımları yer amaktadır. Ayrıca Groups için PowerShell cmdlet'leri de burada liste almaktadır. Çevrimiçi siteleri yönetme hakkında bilgi SharePoint için bkz. [PowerShell SharePoint Online sitelerini yönetme](/sharepoint/manage-team-and-communication-sites-in-powershell).

## <a name="link-to-your-microsoft-365-groups-usage-guidelines"></a>Microsoft 365 Groups kullanım yönergelerinize bağlantı

Kullanıcılar grup [içinde grup oluşturduklarında veya Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), onlara kuruluş kullanım yönergelerinin bir bağlantısını gösterebilirsiniz. Örneğin, grup adına eklenecek belirli bir ön ek veya son ek gerekirse.

Kullanıcılarınızı Azure Active Directory gruplarına yönelik kullanım yönergelerine işaret etmek için Azure Active Directory (Azure AD) PowerShell Microsoft 365 kullanın. Grup [Azure Active Directory yapılandırmak için cmdlet'lere](/azure/active-directory/enterprise-users/groups-settings-cmdlets) göz atabilirsiniz ve kullanım kılavuzu köprüsü tanımlamak için Dizin düzeyinde ayarlar  oluşturma'daki adımları izleyin. AAD cmdlet'ini çalıştırdıktan sonra, bu cmdlet'te bir grup oluşturduklarında veya düzenleyene kadar kullanıcılar yönergelerinizin bağlantısını Outlook.

![Kullanım yönergeleri bağlantısıyla yeni bir grup oluşturun.](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)

![Organizasyonlarınızı grup yönergelerini görmek için Grup kullanımı Office 365 tıklayın.](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)

## <a name="allow-users-to-send-as-the-microsoft-365-group"></a>Kullanıcıların Grup Olarak Göndermesine Microsoft 365 verme

Microsoft 365 gruplarınızı "Farklı Gönder" seçeneğine etkinleştirmek için, bunu yapılandırmak için [Add-RecipientPermission](/powershell/module/exchange/add-recipientpermission) ve [Get-RecipientPermission](/powershell/module/exchange/get-recipientpermission) cmdlet'lerini kullanın. Bu ayarı etkinleştir, Microsoft 365 grup kullanıcıları grup olarak e Outlook veya Web üzerinde Outlook e-posta göndermek ve yanıtlamak için Microsoft 365 kullanabilirler. Kullanıcılar gruba gidebilir, yeni bir e-posta oluşturabilir ve "Farklı Gönder" alanını grubun e-posta adresiyle değiştirebilir.

([Bunu Yönetim Merkezi'nde Exchange.](/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)

Güncelleştirmek istediğiniz grubun diğer *\<GroupAlias\>* adını ve *\<UserAlias\>* izin vermek istediğiniz kullanıcının diğer adıyla değiştirmek üzere aşağıdaki betiği kullanın. [Bağlan betiği çalıştırmak Exchange Online PowerShell'i](/powershell/exchange/connect-to-exchange-online-powershell) çalıştırmayı seçin.

```PowerShell
$groupAlias = "<GroupAlias>"
$userAlias = "<UserAlias>"
$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

Cmdlet çalıştırıldıktan sonra, kullanıcılar Outlook veya Web üzerinde Outlook e-posta adresini From alanına ekleyerek grup olarak göndermek için Adres **Defteri'ne gidebilirler**.

## <a name="create-classifications-for-microsoft-365-groups-in-your-organization"></a>Kuruluş gruplarında Microsoft 365 sınıflandırmaları oluşturma

Kuruluş veya Grup oluşturan kuruluşta yer alan kullanıcıların ayarlarından duyarlılık Microsoft 365 oluşturabilirsiniz. Grupları sınıflandırmak için önceki grup sınıflandırma özelliği yerine duyarlılık etiketleri kullanmalarını öneririz. Duyarlılık etiketlerini kullanma hakkında daha fazla bilgi için bkz. Farklı sitelerde, gruplarda ve Microsoft Teams sitelerde içeriği Microsoft 365 için [duyarlılık SharePoint kullanma](../compliance/sensitivity-labels-teams-groups-sites.md).

> [!IMPORTANT]
> Şu anda sınıflandırma etiketleri kullanıyorsanız, duyarlılık etiketleri etkinleştirildikten sonra grup oluşturan kullanıcılar artık bu etiketleri kullanmayacak.

Önceki grup sınıflandırma özelliğini kullanmaya devamabilirsiniz. Bu sınıflandırmaları, kuruluşta çalışan bir Grup oluşturan kullanıcıların ayar Microsoft 365 oluşturabilirsiniz. Örneğin, kullanıcıların oluşturdukları gruplarda "Standart", "Gizli" ve "Çok Gizli" ayarlamasına izin veebilirsiniz. Grup sınıflandırmaları varsayılan olarak ayar değildir ve kullanıcılarının ayarlayması için sınıflandırmaları oluşturmanız gerekir. Kullanıcılarınızı Azure Active Directory Gruplarına göre kullanım yönergelerine işaret etmek için Microsoft 365 kullanın.

Grup [Azure Active Directory yapılandırmak için cmdlet'lere](/azure/active-directory/users-groups-roles/groups-settings-cmdlets) göz atabilirsiniz ve Microsoft 365 Grupları için sınıflandırma tanımlamak üzere dizin  düzeyinde ayarlar oluşturma sayfasındaki Microsoft 365 izleyin.

```powershell
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

Her sınıflandırmaya bir açıklama ilişkilendirmek için  *ClassificationDescriptions ayarlar özniteliğini kullanarak tanımlayabilirsiniz* .

```powershell
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

Burada Sınıflandırma, ClassificationList'in dizelerini eşler.

Örneğin:

```powershell
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

Yukarıdaki cmdlet'i Azure Active Directory sınıflandırmanızı ayarlamak için, sınıflandırmayı belirli bir grup için ayarlamak istediğiniz zaman [Set-UnifiedGroup](/powershell/module/exchange/Set-UnifiedGroup) cmdlet'ini çalıştırın.

```powershell
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact>
```

Ya da bir sınıflandırmaya sahip yeni bir grup oluşturun.

```powershell
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public>
```

Exchange Online [PowerShell](/powershell/exchange/exchange-online-powershell) kullanma hakkında daha fazla ayrıntı için [Bağlan Exchange Online ve Exchange Online için PowerShell'i Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell) göz atabilirsiniz.

Bu ayarlar etkinleştirildikten sonra, grup sahibi Web üzerinde Outlook'ta açılan menüden bir sınıflandırma seçebilir Outlook düzenle grup sayfasından **kaydedilebilir**.

![Grup sınıflandırması Microsoft 365 seçin.](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)

## <a name="hide-microsoft-365-groups-from-the-global-address-list"></a>Grupları Microsoft 365 adres listesinden gizler.

Bir Grup'un Microsoft 365 adres listesinde (GAL) ve diğer listelerde görünür olup olmadığını belirtebilirsiniz. Örneğin, adres listesinde görünmesini istemiyorsanız, hukuk departmanı grubunuz varsa bu grubun GAL'de görünmesini durdurabilirsiniz. Grubu adres Set-Unified gizlemek için Grup Grubu cmdlet'ini şu şekilde çalıştırın:

```powershell
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-microsoft-365-groups"></a>Gruplarda yalnızca iç kullanıcıların ileti göndermesine Microsoft 365 verme

Başka kuruluşlardan kullanıcıların bir Grup'a e-posta göndermesini Microsoft 365, bu grubun ayarlarını değiştirebilirsiniz. Bu, yalnızca iç kullanıcıların grubunuza e-posta göndermesine olanak sağlar. Dış kullanıcı bu gruba ileti göndermeyi deniyorsa, ileti reddedilir.

Bu ayarı Set-UnifiedGroup için şu cmdlet'i çalıştırın:

```powershell
Set-UnifiedGroup -Identity "Internal senders only" -RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-microsoft-365-groups"></a>Posta Gruplarına Posta Microsoft 365 ekleme

Gönderen bir Grup'a e-posta Microsoft 365 her çalıştığında, onlara bir Posta İpucu gösterebilirsiniz.

Gruba posta Set-Unified için Set-Unified Group cmdlet'ini çalıştırın:

```powershell
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

Posta İpucu ile birlikte, Posta İpucu için başka diller belirten Posta İpucu Çevirileri de belirtebilirsiniz. İspanyolca çevirisini istediğiniz varsayalım, ardından aşağıdaki komutu çalıştırın:

```powershell
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-the-display-name-of-the-microsoft-365-group"></a>Grup Grubu'nda görünen Microsoft 365 değiştirme

Görünen ad, En Son Grubunun Microsoft 365 belirtir. Bu adı yönetim merkeziniz veya <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange merkezinde</a> <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a>. Şu komutu çalıştırarak grubun görünen adını düzenleyebilir veya var olan bir Microsoft 365 Grubu'na görünen ad Set-UnifiedGroup:

```powershell
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-microsoft-365-groups-for-outlook-to-public-or-private"></a>Grup için Grup ayarlarını Microsoft 365 veya Özel Outlook olarak değiştirme

Microsoft 365 Gruplar Outlook varsayılan olarak Özel ayarıyla oluşturulur. Organizasyonunız Varsayılan olarak Microsoft 365 Olarak Oluşturulacak Gruplar (veya Özel ayarına dön) istiyorsa, şu PowerShell cmdlet'i söz dizimini kullanın:

 `Set-OrganizationConfig -DefaultGroupAccessType Public`

Özel olarak ayarlamak için:

 `Set-OrganizationConfig -DefaultGroupAccessType Private`

Ayarı doğrulamak için:

 `Get-OrganizationConfig | ft DefaultGroupAccessType`

Daha fazla bilgi edinmek için [bkz. Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) ve [Get-OrganizationConfig](/powershell/module/exchange/get-organizationconfig).

## <a name="microsoft-365-groups-cmdlets"></a>Microsoft 365 Grupları cmdlet'leri

En son Gruplarda aşağıdaki cmdlet'ler Microsoft 365 kullanılabilir.

|**Cmdlet adı**|**Açıklama**|
|:-----|:-----|
|[Get-UnifiedGroup](/powershell/module/exchange/get-unifiedgroup) <br/> |Varolan grupların görünümünü Microsoft 365 grup nesnesinin özelliklerini görüntülemek için bu cmdlet'i kullanın  <br/> |
|[Set-UnifiedGroup](/powershell/module/exchange/set-unifiedgroup) <br/> |Belirli bir Grup'a Microsoft 365 güncelleştirme  <br/> |
|[New-UnifiedGroup](/powershell/module/exchange/new-unifiedgroup) <br/> |Yeni Grup Microsoft 365 oluşturun. Bu cmdlet en az sayıda parametre sağlar. Genişletilmiş özelliklerin değerlerini ayarlamak için, yeni Set-UnifiedGroup bu grubu oluşturdukta yeni özellikleri kullanın  <br/> |
|[Remove-UnifiedGroup](/powershell/module/exchange/remove-unifiedgroup) <br/> |Var olan bir Microsoft 365 Grubu silme  <br/> |
|[Get-UnifiedGroupLinks](/powershell/module/exchange/get-unifiedgrouplinks) <br/> |Bir Grup için üyelik ve sahip Microsoft 365 alma  <br/> |
|[Add-UnifiedGroupLinks](/powershell/module/exchange/add-unifiedgrouplinks) <br/> |Mevcut Grup Grubuna üye, sahip ve abone Microsoft 365 ekleme <br/> |
|[Remove-UnifiedGroupLinks](/powershell/module/exchange/remove-unifiedgrouplinks) <br/> |Mevcut Grup Grubundan sahipleri ve üyeleri Microsoft 365 kaldırma  <br/> |
|[Get-UserPhoto](/powershell/module/exchange/get-userphoto) <br/> |Bir hesapla ilişkilendirilmiş kullanıcı fotoğrafı hakkında bilgileri görüntülemek için kullanılır. Kullanıcı fotoğrafları Active Directory'de depolanır  <br/> |
|[Set-UserPhoto](/powershell/module/exchange/set-userphoto) <br/> |Kullanıcı fotoğrafını bir hesapla ilişkilendirmek için kullanılır. Kullanıcı fotoğrafları Active Directory'de depolanır  <br/> |
|[Remove-UserPhoto](/powershell/module/exchange/remove-userphoto) <br/> |Bir Grup için fotoğrafı Microsoft 365 kaldırma  <br/> |

## <a name="related-topics"></a>İlgili konular

[Dağıtım listelerini Gruplara Microsoft 365 yükseltme](/office365/admin/manage/upgrade-distribution-lists)

[Gruplarda kimlerin oluştur Microsoft 365 yönetme](/office365/admin/create-groups/manage-creation-of-groups)

[Gruplarda konuk erişimini Microsoft 365 yönetme](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[statik grup üyeliğini dinamik olarak değiştirme](/azure/active-directory/users-groups-roles/groups-change-type)
