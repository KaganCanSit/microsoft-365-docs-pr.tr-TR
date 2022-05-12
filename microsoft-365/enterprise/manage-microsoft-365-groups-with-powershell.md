---
title: PowerShell ile Microsoft 365 Grupları yönetme
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
description: Bu makalede, PowerShell'de Microsoft 365 grupları için yaygın yönetim görevlerini gerçekleştirmeyi öğrenin.
ms.openlocfilehash: 407e242728bf37ebf8c11b8094bfa4931229e4ef
ms.sourcegitcommit: 3226bdf213b290ec5262670873c3a75f17b66ddd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2022
ms.locfileid: "65372213"
---
# <a name="manage-microsoft-365-groups-with-powershell"></a>PowerShell ile Microsoft 365 Grupları yönetme

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Bu makalede, Microsoft PowerShell'de Gruplar için yaygın yönetim görevlerini gerçekleştirme adımları sağlanır. Ayrıca Gruplar için PowerShell cmdlet'lerini listeler. SharePoint sitelerini yönetme hakkında bilgi için bkz. [PowerShell kullanarak SharePoint Çevrimiçi siteleri yönetme](/sharepoint/manage-team-and-communication-sites-in-powershell).

## <a name="link-to-your-microsoft-365-groups-usage-guidelines"></a>Microsoft 365 Grupları kullanım yönergelerinize bağlantı

Kullanıcılar [Outlook'da grup oluşturduğunuzda veya düzenlediklerinde](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), onlara kuruluşunuzun kullanım yönergelerinin bağlantısını gösterebilirsiniz. Örneğin, bir grup adına belirli bir ön ek veya son ek eklenmesi gerekiyorsa.

Kullanıcılarınızı kuruluşunuzun Microsoft 365 gruplarına yönelik kullanım yönergelerine yöneltmek için Azure Active Directory (Azure AD) PowerShell'i kullanın. [Grup ayarlarını yapılandırmak için Azure Active Directory cmdlet'lere](/azure/active-directory/enterprise-users/groups-settings-cmdlets) göz atın ve kullanım kılavuzu köprüsüni tanımlamak için **Dizin düzeyinde ayarlar oluşturma** bölümünde yer alan adımları izleyin. AAD cmdlet'ini çalıştırdığınızda, kullanıcılar Outlook'da grup oluştururken veya düzenlerken yönergelerinizin bağlantısını görür.

![Kullanım yönergeleri bağlantısıyla yeni bir grup oluşturun.](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)

![Kuruluşunuzun grup yönergelerini Office 365 grup yönergelerini görmek için Grup kullanım yönergeleri'ne tıklayın.](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)

## <a name="allow-users-to-send-as-the-microsoft-365-group"></a>Kullanıcıların Microsoft 365 Grubu Olarak Göndermesine İzin Ver

Microsoft 365 gruplarınızın "Farklı Gönder" olarak etkinleştirilmesini istiyorsanız, bunu yapılandırmak için [Add-RecipientPermission](/powershell/module/exchange/add-recipientpermission) ve [Get-RecipientPermission](/powershell/module/exchange/get-recipientpermission) cmdlet'lerini kullanın. Bu ayarı etkinleştirdikten sonra, Microsoft 365 grup kullanıcıları Outlook veya Web üzerinde Outlook kullanarak e-postayı Microsoft 365 grubu olarak gönderebilir ve yanıtlayabilir. Kullanıcılar gruba gidebilir, yeni bir e-posta oluşturabilir ve "Farklı Gönder" alanını grubun e-posta adresiyle değiştirebilir.

([Bunu Exchange Yönetim Merkezi'nde de yapabilirsiniz](/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).)

Öğesini güncelleştirmek istediğiniz grubun diğer adıyla ve *\<UserAlias\>* izin vermek istediğiniz kullanıcının diğer adıyla değiştirerek *\<GroupAlias\>* aşağıdaki betiği kullanın. Bu betiği çalıştırmak [için PowerShell'i Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell) Bağlan.

```PowerShell
$groupAlias = "<GroupAlias>"
$userAlias = "<UserAlias>"
$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

Cmdlet yürütüldükten sonra, kullanıcılar grup e-posta adresini **Kimden** alanına ekleyerek grup olarak göndermek için Outlook veya Web üzerinde Outlook gidebilir.

## <a name="create-classifications-for-microsoft-365-groups-in-your-organization"></a>Kuruluşunuzda Microsoft 365 Grupları için sınıflandırmalar oluşturma

Kuruluşunuzdaki kullanıcıların bir Microsoft 365 Grubu oluştururken ayarlayabileceğiniz duyarlılık etiketleri oluşturabilirsiniz. Grupları sınıflandırmak istiyorsanız, önceki grup sınıflandırma özelliği yerine duyarlılık etiketlerini kullanmanızı öneririz. Duyarlılık etiketlerini kullanma hakkında bilgi için bkz. [Microsoft Teams, Microsoft 365 grupları ve SharePoint sitelerindeki içeriği korumak için duyarlılık etiketlerini kullanma](../compliance/sensitivity-labels-teams-groups-sites.md).

> [!IMPORTANT]
> Şu anda sınıflandırma etiketleri kullanıyorsanız, duyarlılık etiketleri etkinleştirildikten sonra grup oluşturan kullanıcılar artık bu etiketleri kullanamayacaktır.

Önceki grup sınıflandırma özelliğini kullanmaya devam edebilirsiniz. Kuruluşunuzdaki kullanıcıların bir Microsoft 365 Grubu oluştururken ayarlayabileceğiniz sınıflandırmalar oluşturabilirsiniz. Örneğin, kullanıcıların oluşturdukları gruplarda "Standart", "Gizli Dizi" ve "Çok Gizli Dizi" ayarlamasına izin vekleyebilirsiniz. Grup sınıflandırmaları varsayılan olarak ayarlı değildir ve kullanıcılarınızın ayarlaması için bunu oluşturmanız gerekir. Kullanıcılarınızı kuruluşunuzun Microsoft 365 Grupları kullanım yönergelerine yöneltmek için Azure Active Directory PowerShell kullanın.

[Grup ayarlarını yapılandırmak için Azure Active Directory cmdlet'lere](/azure/active-directory/users-groups-roles/groups-settings-cmdlets) göz atın ve Microsoft 365 Grupları sınıflandırmasını tanımlamak için **Dizin düzeyinde ayarlar oluşturma** bölümündeki adımları izleyin.

```powershell
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

Bir açıklamayı her sınıflandırmayla ilişkilendirmek için  *classificationDescriptions* settings özniteliğini kullanarak tanımlayabilirsiniz.

```powershell
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

Burada Sınıflandırma, ClassificationList'teki dizelerle eşleşir.

Örneğin:

```powershell
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

Sınıflandırmanızı ayarlamak için yukarıdaki Azure Active Directory cmdlet'ini çalıştırdıktan sonra, belirli bir grubun sınıflandırmasını ayarlamak istiyorsanız [Set-UnifiedGroup](/powershell/module/exchange/Set-UnifiedGroup) cmdlet'ini çalıştırın.

```powershell
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact>
```

Alternatif olarak, sınıflandırması olan yeni bir grup da oluşturabilirsiniz.

```powershell
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public>
```

[PowerShell'i Exchange Online kullanma hakkında](/powershell/exchange/exchange-online-powershell) daha fazla bilgi [için PowerShell'i Exchange Online ile kullanma ve PowerShell'i Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell) için Bağlan bölümüne bakın.

Bu ayarlar etkinleştirildikten sonra, grup sahibi Web'deki Outlook açılan menüden bir sınıflandırma seçebilir ve Outlook ve grubu **düzenle** sayfasından kaydedebilir.

![Grup sınıflandırması Microsoft 365 seçin.](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)

## <a name="hide-microsoft-365-groups-from-the-global-address-list"></a>Microsoft 365 Grupları genel adres listesinden gizleyin.

Bir Microsoft 365 Grubunun genel adres listesinde (GAL) ve kuruluşunuzdaki diğer listelerde görünüp görünmeyeceğini belirtebilirsiniz. Örneğin, adres listesinde gösterilmesini istemediğiniz bir hukuk departmanı grubunuz varsa, bu grubun GAL'de görünmesini durdurabilirsiniz. Grubu adres listesinden gizlemek için Set-Unified Grubu cmdlet'ini çalıştırın:

```powershell
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-microsoft-365-groups"></a>yalnızca iç kullanıcıların Microsoft 365 Grupları ileti göndermesine izin ver

Diğer kuruluşların kullanıcılarının bir Microsoft 365 Grubuna e-posta göndermesini istemiyorsanız, bu grubun ayarlarını değiştirebilirsiniz. Yalnızca iç kullanıcıların grubunuze e-posta göndermesine izin verir. Dış kullanıcı bu gruba ileti göndermeye çalışırsa reddedilir.

Bu ayarı güncelleştirmek için aşağıdaki gibi Set-UnifiedGroup cmdlet'ini çalıştırın:

```powershell
Set-UnifiedGroup -Identity "Internal senders only" -RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-microsoft-365-groups"></a>Microsoft 365 Grupları'a Posta İpuçları Ekleme

Gönderen bir Microsoft 365 Grubuna e-posta göndermeye çalıştığında, bir Posta İpucu gösterilebilir.

Gruba posta İpucu eklemek için Set-Unified Grubu cmdlet'ini çalıştırın:

```powershell
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

Posta İpucu ile birlikte, Posta İpucu için diğer dilleri belirten MailTipTranslations da ayarlayabilirsiniz. İspanyolca çevirisini almak istediğinizi varsayalım, ardından aşağıdaki komutu çalıştırın:

```powershell
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-the-display-name-of-the-microsoft-365-group"></a>Microsoft 365 Grubunun görünen adını değiştirme

Görünen ad, Microsoft 365 Grubunun adını belirtir. Bu adı <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezinizde</a> veya <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> görebilirsiniz. Set-UnifiedGroup komutunu çalıştırarak grubun görünen adını düzenleyebilir veya mevcut bir Microsoft 365 Grubuna görünen ad atayabilirsiniz:

```powershell
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-microsoft-365-groups-for-outlook-to-public-or-private"></a>Outlook için varsayılan Microsoft 365 Grupları ayarını Genel veya Özel olarak değiştirme

Outlook'daki Microsoft 365 Grupları varsayılan olarak Özel olarak oluşturulur. Kuruluşunuz Microsoft 365 Grupları varsayılan olarak Genel olarak oluşturulmasını istiyorsa (veya Özel'e dönerek) şu PowerShell cmdlet söz dizimini kullanın:

 ```powershell
 Set-OrganizationConfig -DefaultGroupAccessType Public
 ```

Özel olarak ayarlamak için:

 ```powershell
 Set-OrganizationConfig -DefaultGroupAccessType Private
 ```

Ayarı doğrulamak için:

 ```powershell
 Get-OrganizationConfig | ft DefaultGroupAccessType
 ```

Daha fazla bilgi için bkz. [Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) ve [Get-OrganizationConfig](/powershell/module/exchange/get-organizationconfig).

## <a name="microsoft-365-groups-cmdlets"></a>Microsoft 365 Grupları cmdlet'leri

Aşağıdaki cmdlet'ler Microsoft 365 Grupları ile kullanılabilir.

|**Cmdlet adı**|**Açıklama**|
|:-----|:-----|
|[Get-UnifiedGroup](/powershell/module/exchange/get-unifiedgroup) <br/> |Var olan Microsoft 365 Grupları aramak ve grup nesnesinin özelliklerini görüntülemek için bu cmdlet'i kullanın  <br/> |
|[Set-UnifiedGroup](/powershell/module/exchange/set-unifiedgroup) <br/> |Belirli bir Microsoft 365 Grubunun özelliklerini güncelleştirme  <br/> |
|[New-UnifiedGroup](/powershell/module/exchange/new-unifiedgroup) <br/> |Yeni bir Microsoft 365 Grubu oluşturun. Bu cmdlet en az sayıda parametre sağlar. Genişletilmiş özelliklerin değerlerini ayarlamak için yeni grubu oluşturduktan sonra Set-UnifiedGroup kullanın  <br/> |
|[Remove-UnifiedGroup](/powershell/module/exchange/remove-unifiedgroup) <br/> |Mevcut bir Microsoft 365 Grubunu silme  <br/> |
|[Get-UnifiedGroupLinks](/powershell/module/exchange/get-unifiedgrouplinks) <br/> |Microsoft 365 Grubu için üyelik ve sahip bilgilerini alma  <br/> |
|[Add-UnifiedGroupLinks](/powershell/module/exchange/add-unifiedgrouplinks) <br/> |Mevcut bir Microsoft 365 Grubuna üye, sahip ve abone ekleme <br/> |
|[Remove-UnifiedGroupLinks](/powershell/module/exchange/remove-unifiedgrouplinks) <br/> |Mevcut bir Microsoft 365 Grubundan sahipleri ve üyeleri kaldırma  <br/> |
|[Get-UserPhoto](/powershell/module/exchange/get-userphoto) <br/> |Bir hesapla ilişkili kullanıcı fotoğrafı hakkındaki bilgileri görüntülemek için kullanılır. Kullanıcı fotoğrafları Active Directory'de depolanır  <br/> |
|[Set-UserPhoto](/powershell/module/exchange/set-userphoto) <br/> |Kullanıcı fotoğrafını bir hesapla ilişkilendirmek için kullanılır. Kullanıcı fotoğrafları Active Directory'de depolanır  <br/> |
|[Remove-UserPhoto](/powershell/module/exchange/remove-userphoto) <br/> |Microsoft 365 Grubu için fotoğrafı kaldırma  <br/> |

## <a name="related-topics"></a>İlgili konular

[Dağıtım listelerini Microsoft 365 Grupları yükseltme](/office365/admin/manage/upgrade-distribution-lists)

[Kimlerin Microsoft 365 Grupları oluşturabileceğini yönetme](/office365/admin/create-groups/manage-creation-of-groups)

[Microsoft 365 Grupları konuk erişimini yönetme](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[içinde statik grup üyeliğini dinamik olarak değiştirme](/azure/active-directory/users-groups-roles/groups-change-type)
