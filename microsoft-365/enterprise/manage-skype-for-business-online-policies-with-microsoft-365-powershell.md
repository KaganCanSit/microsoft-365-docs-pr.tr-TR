---
title: PowerShell ile Skype Kurumsal Çevrimiçi ilkelerini yönetme
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'Özet: Skype Kurumsal Çevrimiçi kullanıcı hesabı özelliklerinizi ilkelerle yönetmek için PowerShell kullanın.'
ms.openlocfilehash: 71ced77947efda0f587fe7a20af85a73dea73f6c
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094360"
---
# <a name="manage-skype-for-business-online-policies-with-powershell"></a>PowerShell ile Skype Kurumsal Çevrimiçi ilkelerini yönetme

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Skype Kurumsal Online kullanıcı hesabının birçok özelliğini yönetmek için, bunları Microsoft 365 için PowerShell ile ilkelerin özellikleri olarak belirtmeniz gerekir.
  
## <a name="before-you-begin"></a>Başlamadan önce

Komutları çalıştıracak şekilde ayarlamak için bu yönergeleri kullanın (daha önce tamamlamış olduğunuz adımları atlayın):

  > [!Note]
  > Skype Kurumsal Online Connector şu anda en son Teams PowerShell modülünün bir parçasıdır. PowerShell genel sürümünün en son Teams kullanıyorsanız, Skype Kurumsal Çevrimiçi Bağlayıcı'yı yüklemeniz gerekmez.

1. [Teams PowerShell modülünü](/microsoftteams/teams-powershell-install) yükleyin.
    
2. bir Windows PowerShell komut istemi açın ve aşağıdaki komutları çalıştırın: 

   ```powershell
   Import-Module MicrosoftTeams
   $userCredential = Get-Credential
   Connect-MicrosoftTeams -Credential $userCredential
   ```

   İstendiğinde, Skype Kurumsal Çevrimiçi yönetici hesabı adınızı ve parolanızı girin.
    
## <a name="manage-user-account-policies"></a>Kullanıcı hesabı ilkelerini yönetme

Birçok Skype Kurumsal Çevrimiçi kullanıcı hesabı özelliği ilkeler kullanılarak yapılandırılır. İlkeler yalnızca bir veya daha fazla kullanıcıya uygulanabilen ayar koleksiyonlarıdır. İlkenin nasıl yapılandırıldığına bakmak için FederationAndPICDefault ilkesi için şu örnek komutu çalıştırabilirsiniz:
  
```powershell
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

Buna karşılık, şuna benzer bir şey geri almanız gerekir:
  
```powershell
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

Bu örnekte, bu ilkedeki değerler, federasyon kullanıcılarıyla iletişim söz konusu olduğunda bir kullanımın neler yapabileceğini veya yapamayacağını belirler. Örneğin, bir kullanıcının kuruluş dışındaki kişilerle iletişim kurabilmesi için EnableOutsideAccess özelliğinin True olarak ayarlanması gerekir. Bu özelliğin Microsoft 365 yönetim merkezi görünmediğini unutmayın. Bunun yerine, yaptığınız diğer seçimlere bağlı olarak özellik otomatik olarak True veya False olarak ayarlanır. İlgilenen diğer iki özellik şunlardır:
  
- **EnableFederationAccess** , kullanıcının federasyon etki alanlarından kişilerle iletişim kurup kuramayacağını gösterir.
    
- **EnablePublicCloudAccess**, kullanıcının Windows Canlı kullanıcılarla iletişim kurup kuramayacağını gösterir.
    
Bu nedenle, kullanıcı hesaplarında federasyonla ilgili özellikleri doğrudan değiştirmezsiniz (örneğin, **Set-CsUser -EnableFederationAccess $True**). Bunun yerine, bir hesaba istenen özellik değerlerinin önceden yapılandırılmış olduğu bir dış erişim ilkesi atarsınız. Bir kullanıcının federasyon kullanıcılarıyla ve Windows Canlı kullanıcılarla iletişim kurabilmesini istiyorsak, bu kullanıcı hesabına bu tür iletişimlere izin veren bir ilke atanmalıdır.
  
Birinin kuruluş dışındaki kullanıcılarla iletişim kurup kuramadığını öğrenmek istiyorsanız şunları yapabilirsiniz:
  
- Bu kullanıcıya hangi dış erişim ilkesinin atandığını belirleyin.
    
- bu ilke tarafından izin verilen veya izin verilmeyen özellikleri belirleyin.
    
Örneğin, bu komutu kullanarak bunu yapabilirsiniz:
  
```powershell
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

Bu komut kullanıcıya atanan ilkeyi bulur ve ardından bu ilke içinde etkinleştirilmiş veya devre dışı bırakılmış özellikleri bulur.
  
PowerShell ile Skype Kurumsal Çevrimiçi ilkelerini yönetmek için aşağıdaki cmdlet'lere bakın:

- [İstemci ilkesi](/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)
- [Konferans ilkesi](/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)
- [Mobil ilke](/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)
- [Çevrimiçi Sesli Mesaj ilkesi](/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)
- [Ses Yönlendirme ilkesi](/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)


> [!NOTE]
> Skype Kurumsal Çevrimiçi arama planı, ad dışında her açıdan bir ilkedir. Office Communications Server ve Exchange ile geriye dönük uyumluluk sağlamak için "arama ilkesi" yerine "arama planı" adı seçildi. 
  
Örneğin, kullanımınıza sunulan tüm ses ilkelerine bakmak için şu komutu çalıştırın:
  
```powershell
Get-CsVoicePolicy
```

> [!NOTE]
> Bu, kullanabileceğiniz tüm ses ilkelerinin listesini döndürür. Ancak tüm ilkelerin tüm kullanıcılara atanamadığını unutmayın. Bunun nedeni lisanslama ve coğrafi konum gibi çeşitli kısıtlamalardır. ("[Kullanım konumu](/previous-versions/azure/dn194136(v=azure.100))" olarak adlandırılır.) Dış erişim ilkelerini ve belirli bir kullanıcıya atanabilecek konferans ilkelerini bilmek istiyorsanız, aşağıdakine benzer komutları kullanın: 

```powershell
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

ApplicableTo parametresi, döndürülen verileri belirtilen kullanıcıya atanabilecek ilkeler ile sınırlar (örneğin, Alex Darrow). Lisanslama ve kullanım konumu kısıtlamalarına bağlı olarak, kullanılabilir tüm ilkelerin bir alt kümesini temsil edebilir. 
  
Bazı durumlarda, ilkelerin özellikleri Microsoft 365 ile kullanılmazken, diğerleri yalnızca Microsoft destek personeli tarafından yönetilebilir. 
  
Skype Kurumsal Online ile kullanıcıların bir tür ilke tarafından yönetilmesi gerekir. İlkeyle ilgili geçerli bir özellik boşsa bu, söz konusu kullanıcının bir genel ilke tarafından yönetildiği anlamına gelir. Bu, kullanıcıya özel olarak kullanıcı başına ilke atanmadığı sürece otomatik olarak uygulanan bir ilkedir. Kullanıcı hesabı için listelenen bir istemci ilkesi görmediğimiz için genel ilke tarafından yönetilir. Genel istemci ilkesini şu komutla belirleyebilirsiniz:
  
```powershell
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a>Ayrıca bkz.

[PowerShell ile Skype Kurumsal Online'i yönetme](manage-skype-for-business-online-with-microsoft-365-powershell.md)
  
[PowerShell ile Microsoft 365’i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
  
[Microsoft 365 için PowerShell'i kullanmaya başlama](getting-started-with-microsoft-365-powershell.md)