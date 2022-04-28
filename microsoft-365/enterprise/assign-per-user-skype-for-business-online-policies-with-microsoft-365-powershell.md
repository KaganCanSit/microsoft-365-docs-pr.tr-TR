---
title: Microsoft 365 için PowerShell ile kullanıcı başına Skype Kurumsal Çevrimiçi ilkeleri atama
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'Özet: Skype Kurumsal Online ilkeleriyle kullanıcı başına iletişim ayarlarını atamak için Microsoft 365 için PowerShell kullanın.'
ms.openlocfilehash: 70120f6d296f958f44906a3526a7dcaa36b7eb04
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091401"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-powershell-for-microsoft-365"></a>Microsoft 365 için PowerShell ile kullanıcı başına Skype Kurumsal Çevrimiçi ilkeleri atama

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Microsoft 365 için PowerShell kullanmak, Skype Kurumsal Çevrimiçi ilkeleriyle kullanıcı başına iletişim ayarlarını atamanın etkili bir yoludur.
  
## <a name="prepare-to-run-the-powershell-commands"></a>PowerShell komutlarını çalıştırmaya hazırlanma

Komutları çalıştıracak şekilde ayarlamak için bu yönergeleri kullanın (daha önce tamamlamış olduğunuz adımları atlayın):
  
  > [!Note]
   > Skype Kurumsal Online Connector şu anda en son Teams PowerShell modülünün bir parçasıdır. PowerShell genel sürümünün en son Teams kullanıyorsanız, Skype Kurumsal Çevrimiçi Bağlayıcı'yı yüklemeniz gerekmez.

1. [Teams PowerShell modülünü](/microsoftteams/teams-powershell-install) yükleyin.
    
2. bir Windows PowerShell komut istemi açın ve aşağıdaki komutları çalıştırın: 
    
   ```powershell
   Import-Module MicrosoftTeams
   Connect-MicrosoftTeams
   ```

   İstendiğinde, Skype Kurumsal Çevrimiçi yönetici hesabı adınızı ve parolanızı girin.
    
## <a name="updating-external-communication-settings-for-a-user-account"></a>Kullanıcı hesabı için dış iletişim ayarlarını güncelleştirme

Bir kullanıcı hesabındaki dış iletişim ayarlarını değiştirmek istediğinizi varsayalım. Örneğin, Alex'in federasyon kullanıcılarıyla iletişim kurmasına izin vermek istiyorsunuz (EnableFederationAccess True'ya eşittir) ancak Windows Canlı kullanıcılarla iletişim kurmazsınız (EnablePublicCloudAccess eşittir False). Bunu yapmak için iki şey yapmanız gerekir:
  
1. Ölçütlerimizi karşılayan bir dış erişim ilkesi bulun.
    
2. Bu dış erişim ilkesini Alex'e atayın.
    
Alex'e hangi dış erişim ilkesinin atandığını nasıl belirlersiniz? Aşağıdaki komut, EnableFederationAccess değerinin True ve EnablePublicCloudAccess'in False olarak ayarlandığı tüm dış erişim ilkelerini döndürür:
  
```powershell
Get-CsExternalAccessPolicy -Include All| Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

ExternalAccessPolicy'nin herhangi bir özel örneğini oluşturmadığınız sürece, bu komut ölçütlerimizi (FederationOnly) karşılayan bir ilke döndürür. Aşağıda bir örnek verilmiştir:
  
```powershell
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

Alex'e hangi ilkenin atandığını bildiğinize göre, [Grant-CsExternalAccessPolicy](/powershell/module/skype/Get-CsExternalAccessPolicy) cmdlet'ini kullanarak bu ilkeyi atayabiliriz. Aşağıda bir örnek verilmiştir:
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

İlke atamak oldukça basittir: Yalnızca kullanıcının kimliğini ve atanacak ilkenin adını belirtirsiniz. 
  
İlkeler ve ilke atamaları söz konusu olduğunda, kullanıcı hesaplarıyla tek tek çalışmakla sınırlı değilsiniz. Örneğin, federasyon iş ortaklarıyla ve Windows Canlı kullanıcılarla iletişim kurmasına izin verilen tüm kullanıcıların listesine ihtiyacınız olduğunu varsayalım. Bu kullanıcılara FederationAndPICDefault dış kullanıcı erişim ilkesi atandığını zaten biliyoruz. Bunu bildiğimiz için, tek bir basit komut çalıştırarak tüm bu kullanıcıların listesini görüntüleyebilirsiniz. Komut şu şekildedir:
  
```powershell
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

Başka bir deyişle, ExternalAccessPolicy özelliğinin FederationAndPICDefault olarak ayarlandığı tüm kullanıcıları bize gösterin. (Ekranda görünen bilgi miktarını sınırlamak için Select-Object cmdlet'ini kullanarak bize yalnızca her kullanıcının görünen adını gösterin.) 
  
Tüm kullanıcı hesaplarımızı aynı ilkeyi kullanacak şekilde yapılandırmak için şu komutu kullanın:
  
```powershell
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

Bu komut, Lync için etkinleştirilen tüm kullanıcıların koleksiyonunu döndürmek için Get-CsOnlineUser kullanır, ardından tüm bu bilgileri Grant-CsExternalAccessPolicy'ye gönderir ve bu da koleksiyondaki her kullanıcıya FederationAndPICDefault ilkesini atar.
  
Ek bir örnek olarak, Daha önce Alex'e FederationAndPICDefault ilkesi atadığınız ve şimdi fikrinizi değiştirdiğiniz ve genel dış erişim ilkesi tarafından yönetilmesini istediğinizi varsayalım. Genel ilkeyi herkese açıkça atayamazsınız. Bunun yerine, kullanıcı başına ilke atanmamışsa, genel ilke belirli bir kullanıcı için kullanılır. Bu nedenle, Alex'in genel ilke tarafından yönetilmesini istiyorsak, daha önce kendisine atanmış olan kullanıcı başına ilke  *atamasını kaldırmanız*  gerekir. Aşağıda örnek bir komut verilmiştir:
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

Bu komut, Alex'e atanan dış erişim ilkesinin adını null bir değere ($Null) ayarlar. Null , "hiçbir şey" anlamına gelir. Başka bir deyişle, Alex'e dış erişim ilkesi atanmadı. Bir kullanıcıya dış erişim ilkesi atanmadığında, bu kullanıcı genel ilke tarafından yönetilir.

## <a name="managing-large-numbers-of-users"></a>Çok sayıda kullanıcıyı yönetme

Çok sayıda kullanıcıyı (1000 veya daha fazla) yönetmek için [Invoke-Command](/powershell/module/microsoft.powershell.core/invoke-command) cmdlet'ini kullanarak komutları bir betik bloğu aracılığıyla toplu işlemeniz gerekir.  Önceki örneklerde, bir cmdlet her yürütildiğinde çağrıyı ayarlamalı ve ardından geri göndermeden önce sonucu beklemelidir.  Betik bloğu kullanılırken, bu cmdlet'lerin uzaktan yürütülmesine ve tamamlandıktan sonra verileri geri göndermesine olanak tanır.

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

Bu, bir kerede istemci ilkesi olmayan 500 kullanıcı bulur. Onlara "ClientPolicyNoIMURL" istemci ilkesini ve "FederationAndPicDefault" dış erişim ilkesini verir. Sonuçlar 50'lik gruplar halinde toplu olarak oluşturulur ve 50'lik her toplu iş uzak makineye gönderilir.
  
## <a name="see-also"></a>Ayrıca bkz.

[PowerShell ile Skype Kurumsal Online'i yönetme](manage-skype-for-business-online-with-microsoft-365-powershell.md)
  
[PowerShell ile Microsoft 365’i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Microsoft 365 için PowerShell'i kullanmaya başlama](getting-started-with-microsoft-365-powershell.md)
