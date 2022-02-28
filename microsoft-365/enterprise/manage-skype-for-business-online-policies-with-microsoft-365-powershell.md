---
title: PowerShell Skype Kurumsal Online ilkelerini yönetme
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 'Özet: İlkelerle birlikte Skype Kurumsal Online kullanıcı hesabı özelliklerinizi yönetmek için PowerShell kullanın.'
ms.openlocfilehash: 674ea6daba498279537f7c302f4bf4d791ee00f5
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985147"
---
# <a name="manage-skype-for-business-online-policies-with-powershell"></a>PowerShell Skype Kurumsal Online ilkelerini yönetme

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Skype Kurumsal Online'da kullanıcı hesabının birçok özelliklerini yönetmek için, bunları Microsoft 365 için PowerShell ile ilkeler özellikleri olarak belirtmelisiniz.
  
## <a name="before-you-begin"></a>Başlamadan önce

Komutları çalıştırmak üzere ayarlamak için bu yönergeleri kullanın (zaten tamamlamış durumda olan adımları atlayabilirsiniz):

  > [!Note]
  > Skype Kurumsal Online Connector şu anda en son PowerShell modülünde Teams vardır. En son PowerShell Teams kullanıyorsanız, Skype Kurumsal Online Connector'ı yüklemenize gerek yok.

1. [Teams PowerShell modülünü yükleyin](/microsoftteams/teams-powershell-install).
    
2. Windows PowerShell komut istemini açın ve aşağıdaki komutları çalıştırın: 

   ```powershell
   Import-Module MicrosoftTeams
   $userCredential = Get-Credential
   Connect-MicrosoftTeams -Credential $userCredential
   ```

   İstendiğinde, Çevrimiçi Skype Kurumsal hesap adı ve parolanızı girin.
    
## <a name="manage-user-account-policies"></a>Kullanıcı hesabı ilkelerini yönetme

Birçok Skype Kurumsal Online kullanıcı hesabı özellikleri ilkeler kullanılarak yapılandırılır. İlkeler, yalnızca bir veya birden çok kullanıcıya uygulanan ayarlar koleksiyonudur. İlkenin nasıl yapılandırıldığından bakmak için, FederationAndPICDefault ilkesi için bu örnek komutu çalıştırabilirsiniz:
  
```powershell
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

Böylece, aşağıdakine benzer bir şey dönmeli:
  
```powershell
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

Bu örnekte, bu ilkenin içindeki değerler, federasyon kullanıcıleriyle iletişim kurma gibi bir iletişim söz konusu olduğunda, bir kullanımın neler yapacı veya neleri yapa olmadığını belirler. Örneğin, kullanıcının kuruluş dışındaki kullanıcılarla iletişim kur olması için EnableOutsideAccess özelliğinin True olarak ayarlanmış olması gerekir. Bu özelliğin her iki ekranda da Microsoft 365 yönetim merkezi. Bunun yerine, kendi yapılan diğer seçimler temel alarak özellik otomatik olarak Doğru veya Yanlış değerine ayarlanır. Diğer ilgili iki özellik de şu şekildedir:
  
- **EnableFederationAccess** , kullanıcının federasyon etki alanlarındaki kullanıcılarla iletişim kurıp kuramayacağını gösterir.
    
- **EnablePublicCloudAccess**, kullanıcının canlı kullanıcılarla iletişim kuramayacağını Windows gösterir.
    
Bu nedenle, kullanıcı hesaplarda federasyonla ilgili özellikleri doğrudan değiştirmezsiniz (örneğin, **Set-CsUser -EnableFederationAccess $True**). Bunun yerine, istenen özellik değerlerinin önceden yapılandırılması için bir hesaba dış erişim ilkesi atarsınız. Bir kullanıcının federasyon kullanıcıleriyle ve Windows Live kullanıcıleriyle iletişim kura uygun olması için, o kullanıcı hesabına bu tür iletişimlere izin veren bir ilke atanmış olması gerekir.
  
Bir kişinin kuruluş dışındaki kullanıcılarla iletişim kurıp kuramayay bilmek için:
  
- Bu kullanıcıya hangi dış erişim ilkesi atandığı belirleme.
    
- Bu ilke hangi özelliklere izin verilmiyor veya hangi özelliklere izin verilmemektedir.
    
Örneğin, şu komutu kullanarak bunuabilirsiniz:
  
```powershell
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

Bu komut kullanıcıya atanan ilkeyi bulur, sonra da bu ilke içinde etkinleştirilen veya devre dışı bırakılmış özellikleri bulur.
  
PowerShell ile Skype Kurumsal Online ilkelerini yönetmek için, aşağıdaki cmdlet'lere bakın:

- [İstemci ilkesi](/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)
- [Konferans ilkesi](/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)
- [Mobil ilke](/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)
- [Çevrimiçi Sesli Mesaj ilkesi](/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)
- [Ses Yönlendirme ilkesi](/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)


> [!NOTE]
> Çevrimiçi Skype Kurumsal arama planı, ad dışında her açıdan bir ilkedir. Office Communications Server ile geriye dönük uyumluluk sağlamak için, diyelim ki "arama ilkesi" yerine "arama planı" Exchange. 
  
Örneğin, kullanımınıza yönelik tüm ses ilkelerine bakmak için şu komutu çalıştırın:
  
```powershell
Get-CsVoicePolicy
```

> [!NOTE]
> Bu, size kullanılabilen tüm ses ilkelerinin listesini döndürür. Bununla birlikte, tüm ilkelerin tüm kullanıcılara atanana olmadığını da unutmayın. Bu durum lisans ve coğrafi konumun da katıldığı çeşitli kısıtlamalardan dolayı meydana geldi. ("Kullanım konumu[" olarak adlandırılır](/previous-versions/azure/dn194136(v=azure.100)).) Belirli bir kullanıcıya atanabilir dış erişim ilkelerini ve konferans ilkelerini bilmek için aşağıdakine benzer komutları kullanın: 

```powershell
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

ApplicableTo parametresi, döndürülen verileri belirtilen kullanıcıya atanacak ilkelere (örneğin, Alex Darrow) sınırlar. Lisans ve kullanım konumu kısıtlamalarına bağlı olarak, kullanılabilir tüm ilkelerin bir alt kümesini temsil ediyor olabilir. 
  
Bazı durumlarda, ilke özellikleri diğer çalışanlarla Microsoft 365, diğerleri ise yalnızca Microsoft destek personeli tarafından yönetilebilir. 
  
Skype Kurumsal Online ile, kullanıcıların bazı tür ilkelerle yönetilleri gerekir. Geçerli bir ilkeyle ilgili özellik boşsa, söz konusu kullanıcıya özel olarak bir kullanıcı ilkesi atanmadığı sürece otomatik olarak kullanıcıya uygulanan bir ilke olan genel bir ilke söz konusu olur. Kullanıcı hesabı için listelenen bir istemci ilkesi göre görmemiz, genel ilke tarafından yönetiliyor. Genel istemci ilkesine şu komutu kullanarak karar veabilirsiniz:
  
```powershell
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a>Ayrıca bkz.

[PowerShell Skype Kurumsal Online'i yönetme](manage-skype-for-business-online-with-microsoft-365-powershell.md)
  
[PowerShell Microsoft 365'i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Microsoft 365 için PowerShell ile çalışmaya Microsoft 365](getting-started-with-microsoft-365-powershell.md)