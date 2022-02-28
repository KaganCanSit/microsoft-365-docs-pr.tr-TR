---
title: Kullanıcı başına PowerShell Skype Kurumsal Online ilkeleri atama Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/16/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: 'Özet: Skype Kurumsal Online ilkeleri Microsoft 365 yle kullanıcı başına iletişim ayarlarını atamak üzere Skype Kurumsal için PowerShell kullanın.'
ms.openlocfilehash: c49d465ffe0a6f1379681be0ae4faaf9982b6ef0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985315"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-powershell-for-microsoft-365"></a>Kullanıcı başına PowerShell Skype Kurumsal Online ilkeleri atama Microsoft 365

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Microsoft 365 için PowerShell kullanmak, Skype Kurumsal Online ilkeleriyle kullanıcı başına iletişim ayarları atamanın Skype Kurumsal bir yolu olur.
  
## <a name="prepare-to-run-the-powershell-commands"></a>PowerShell komutlarını çalıştırmaya hazırlanma

Komutları çalıştırmak üzere ayarlamak için bu yönergeleri kullanın (zaten tamamlamış durumda olan adımları atlayabilirsiniz):
  
  > [!Note]
   > Skype Kurumsal Online Connector şu anda en son PowerShell modülünde Teams vardır. En son PowerShell Teams kullanıyorsanız, Skype Kurumsal Online Connector'ı yüklemenize gerek yok.

1. [Teams PowerShell modülünü yükleyin](/microsoftteams/teams-powershell-install).
    
2. Windows PowerShell komut istemini açın ve aşağıdaki komutları çalıştırın: 
    
   ```powershell
   Import-Module MicrosoftTeams
   Connect-MicrosoftTeams
   ```

   İstendiğinde, Çevrimiçi Skype Kurumsal hesap adı ve parolanızı girin.
    
## <a name="updating-external-communication-settings-for-a-user-account"></a>Kullanıcı hesabı için dış iletişim ayarlarını güncelleştirme

Kullanıcı hesabı üzerinde dış iletişim ayarlarını değiştirmek istediğiniz varsayalım. Örneğin, Alex'in federasyon kullanıcıleriyle iletişim kurmasına izin vermek istiyor (EnableFederationAccess eşittir True) ancak Windows Live kullanıcıleriyle (EnablePublicCloudAccess eşittir False) iletişim kurmasına izin vermek istiyor olun. Bunu yapmak için iki şey yapmak gerekir:
  
1. Ölçütlerimize uyan bir dış erişim ilkesi bulun.
    
2. Dış erişim ilkesi Alex'e attayn.
    
Alex'e hangi dış erişim ilkesi atamayı nasıl belirlersiniz? Aşağıdaki komut EnableFederationAccess'in True olarak ve EnablePublicCloudAccess'in False olarak ayar bulunduğu tüm dış erişim ilkelerini döndürür:
  
```powershell
Get-CsExternalAccessPolicy -Include All| Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

ExternalAccessPolicy'nin herhangi bir özel örneğini oluşturmadıysanız, bu komut ölçütlerimize uyan bir ilke döndürür (FederationOnly). İşte bir örnek:
  
```powershell
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

Artık Alex'e hangi ilkeyi atayacağız biliyorsunuz, [Grant-CsExternalAccessPolicy](/powershell/module/skype/Get-CsExternalAccessPolicy) cmdlet'ini kullanarak bu ilkeyi atacağız. İşte bir örnek:
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

İlke atamak oldukça basittir: Yalnızca Kullanıcının Kimliğini ve atanacak ilkenin adını belirtirsiniz. 
  
İlkeler ve ilke atamaları söz konusu olduğunda, kullanıcı hesaplarıyla tek tek çalışmak zorunda da olmazsınız. Örneğin, federasyon ortaklarıyla ve diğer canlı kullanıcılarla iletişim kurmasına izin verilen tüm kullanıcıların bir listesine ihtiyacınız Windows varsayalım. Bu kullanıcılara dış kullanıcı erişimi ilkesi FederationAndPICDefault atanmış olduğunu zaten biliyoruz. Bunun nedeni, tek bir basit komut çalıştırarak tüm bu kullanıcıların listesini görüntüley bilmektir. Komut şöyledir:
  
```powershell
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

Başka bir deyişle, ExternalAccessPolicy özelliğinin FederationAndPICDefault olarak ayar bulunduğu tüm kullanıcıları bize göster. (Ayrıca, ekranda görünen bilgi miktarını sınırlamak için, Select-Object cmdlet'ini kullanarak yalnızca her kullanıcının görünen adını gösterebilirsiniz.) 
  
Tüm kullanıcı hesaplarımızı aynı ilkeyi kullanmak üzere yapılandırmak için şu komutu kullanın:
  
```powershell
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

Bu komut Get-CsOnlineUser'i kullanarak Lync için etkinleştirilmiş olan tüm kullanıcıların koleksiyonunu gönderir ve ardından tüm bilgileri Grant-CsExternalAccessPolicy'ne gönderir ve bu da koleksiyonda yer alan her kullanıcıya FederationAndPICDefault ilkesi atar.
  
Ek bir örnek olarak, daha önce Alex'e FederationAndPICDefault ilkesi atadığı ve şimdi de fikirlerinizi değiştirdiğini ve bu ilkenin genel dış erişim ilkesi tarafından yönetilsin mi olduğunu varsayalım. Genel ilkeyi açıkça kimseye atayayaz. Bunun yerine, kullanıcıya herhangi bir kullanıcı başına ilke atanmamışsa, o kullanıcı için genel ilke kullanılır. Bu nedenle, Alex'in genel ilke tarafından yönetilsin mi diye önceden bu ilkeye atanan kullanıcı başına atamayı devre dışı bıraksanız gerekir. İşte örnek bir komut:
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

Bu komut Alex'e atanan dış erişim ilkesi adını null değere (veya $Null). Null "hiçbir şey" anlamına gelir. Başka bir deyişle, Alex'e hiçbir dış erişim ilkesi atanmamıştır. Kullanıcıya dış erişim ilkesi atanmamışsa, bu kullanıcı bundan sonra genel ilke tarafından yönetilir.

## <a name="managing-large-numbers-of-users"></a>Çok fazla sayıda kullanıcının yönetimi

Çok büyük sayılarda kullanıcıları (1000 veya daha fazla) yönetmek için [, Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet'ini kullanarak komutları bir betik bloğu aracılığıyla toplu hale yönetmeniz gerekir.  Önceki örneklerde, bir cmdlet her yürütülse, çağrıyı ayarlaması ve ardından sonucu göndermeden önce beklemesi gerekir.  Betik bloğu kullanılırken, bu cmdlet'lerin uzaktan yürütülmelerini ve tamamlandığında verileri geri göndermelerini sağlar.

```powershell
$s = Get-PSSession | Where-Object { ($.ComputerName -like '*.online.lync.com' -or $.Computername -eq 'api.interfaces.records.teams.microsoft.com') -and $.State -eq 'Opened' -and $.Availability -eq 'Available' }

$users = Get-CsOnlineUser -Filter { ClientPolicy -eq $null } -ResultSize 500

$batch = 50
$filter = ''
$total = $users.Count
$count = 0
    $users | ForEach-Object {
    $upn = $_.UserPrincipalName
    $filter += "(UserPrincipalName -eq '$upn')"
    $batch--
    $count++
    if (($batch -eq 0) -or ($count -eq $total)) {
        $filterSB=[ScriptBlock]::Create($filter)
        Invoke-Command -Session $s -ScriptBlock {param($f) Get-CsOnlineUser -filter $f | Grant-CsClientPolicy -PolicyName "ClientPolicyNoIMURL" -Passthru | Grant-CsExternalAccessPolicy -PolicyName "FederationAndPICDefault"} -ArgumentList $filterSB

        # Reset
        $batch = 50
        $filter = ''
    } else {
        $filter += " -or "
    }
}
```

Bu, aynı anda istemci ilkesine sahip değilken 500 kullanıcı bulur. Onlara "ClientPolicyNoIMURL" istemci ilkesi ve dış erişim ilkesi "FederationAndPicDefault" iznini ve ardından da "FederationAndPicDefault" istemci ilkesi sağlar. Sonuçlar 50'den fazla grup halinde toplu işler ve 50'nin her toplu işlemi uzak makineye gönderilir.
  
## <a name="see-also"></a>Ayrıca bkz.

[PowerShell Skype Kurumsal Online'i yönetme](manage-skype-for-business-online-with-microsoft-365-powershell.md)
  
[PowerShell Microsoft 365'i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Microsoft 365 için PowerShell ile çalışmaya Microsoft 365](getting-started-with-microsoft-365-powershell.md)
