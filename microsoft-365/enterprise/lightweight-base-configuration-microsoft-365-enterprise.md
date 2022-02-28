---
title: Hafif taban yapılandırması
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/14/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
- seo-marvel-apr2020
- admindeeplinkMAC
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: Kurumsal test test ortamı oluşturmak için bu Test Laboratuvarı Kılavuzunu Microsoft 365 kullanın.
ms.openlocfilehash: 742fc93b64d2e3c1d858931eb7dbc591ebcd8e9d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62977696"
---
# <a name="the-lightweight-base-configuration"></a>Hafif taban yapılandırması

*Bu Test Laboratuvarı Kılavuzu, hem kurumsal hem de Microsoft 365 test ortamları için Office 365 Kurumsal kullanılabilir.*

Bu makalede, Microsoft 365 E5 aboneliği ve çalışan bir bilgisayar ile basitleştirilmiş bir ortamın nasıl oluşturulacakları Windows 10 Enterprise.

![Hafif bir Microsoft 3656 Enterprise ortamıdır.](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase4.png)

Basit bir test ortamı oluşturmak beş aşama içerir:
- [Aşama 1: Microsoft 365 E5 aboneliğinizi oluşturma](#phase-1-create-your-microsoft-365-e5-subscription)
- [Aşama 2: Office 365 deneme aboneliğinizi yapılandırma](#phase-2-configure-your-office-365-trial-subscription)
- [Aşama 3: Deneme Microsoft 365 E5 ekleme](#phase-3-add-a-microsoft-365-e5-trial-subscription)
- [Aşama 4: Windows 10 Enterprise oluşturma](#phase-4-create-a-windows-10-enterprise-computer)
- [Aşama 5: Bilgisayarınızdan Azure AD Windows 10 e katılma](#phase-5-join-your-windows-10-computer-to-azure-ad)

Sonuçta elde edilen ortamı, kurumsal özelliklerle ilgili özelliklerin ve [işlevlerin Microsoft 365 kullanın](https://www.microsoft.com/microsoft-365/enterprise).

![Microsoft bulutu için Test Laboratuvarı Kılavuzları.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)
  
> [!TIP]
> Kurumsal Test Laboratuvarı Kılavuzu yığınına göre Microsoft 365 görsel bir harita için bkz. [Microsoft 365 Test Laboratuvarı Kılavuzu Yığını](../downloads/Microsoft365EnterpriseTLGStack.pdf).

>[!NOTE]
>Deneme aboneliğinizin 30 günü içinde bu ortamda size gereken belirli bilgileri kaydetmek için bu makaleyi Office 365 edebilirsiniz. Trail aboneliğini 30 gün daha uzatabilirsiniz. Kalıcı bir test ortamı için, ayrı bir Azure AD kiracısı ve az sayıda lisansla ücretli yeni bir abonelik oluşturun.

## <a name="phase-1-create-your-microsoft-365-e5-subscription"></a>Aşama 1: Microsoft 365 E5 aboneliğinizi oluşturma

Microsoft 365 E5 deneme aboneliğiyle başlar ve Microsoft 365 E5 aboneliğini ekleriz.

>[!NOTE]
>Test ortamınız şu anda ücretli tüm abonelikler için Office 365 Azure AD kiracısına sahip olmak için deneme sürümü aboneliği oluşturmanızı öneririz. Bu ayrım, üretim aboneliklerinizi etkilemeden test kiracısına kullanıcı ve grup ekleyebileceksiniz anlamına gelir.

Deneme aboneliğinizi Microsoft 365 E5 için, önce hayali bir şirket adı ve yeni bir Microsoft hesabınız gerekir.
  
1. Microsoft örnek içeriğinde kullanılan kurgusal bir şirket adı olan ancak bu gerekli olmayan şirket adı olarak Contoso şirket adının bir çeşitlesini öneririz. Kurgusal şirket adını buraya yazın: ![Satır.](../media/Common-Images/TableLine.png)
    
2. Yeni bir Microsoft hesabına kaydolmak için, yeni bir [https://outlook.com](https://outlook.com) e-posta hesabı ve adresi olan bir hesap oluşturun ve bu hesabı açın. Bir hesaba kaydolmak için bu hesabı Office 365.
    
    - Yeni hesap adı ve soyadınızı buraya yazın: ![Satır.](../media/Common-Images/TableLine.png)
    
    - Yeni e-posta hesabı adresini buraya yazın: ![Satır.](../media/Common-Images/TableLine.png)@outlook.com
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a>Office 365 E5 deneme aboneliğine kaydolma

1. Tarayıcınızda' gidin [https://aka.ms/e5trial](https://aka.ms/e5trial).
    
2. Teşekkür teşekkürler sayfasının 1 **. adımına Office 365 E5** e-posta adresinizi girin.
3. İzli abonelik işleminin 2. adıma, istenen bilgileri girin ve ardından doğrulamayı gerçekleştirin.
4. 3. adımda, bir kuruluş adı ve sonra da aboneliğin genel yöneticisi olacak hesap adını girin.
5. 4. adım için, oturum açma sayfasını buraya ekleyin (seçin ve kopyalayın): ![Satır.](../media/Common-Images/TableLine.png)
6. Kullanıcı kimliğini buraya girin: ![Satır.](../media/Common-Images/TableLine.png). onmicrosoft.com  
   Güvenli bir konuma girdiğiniz parolayı kaydetme.
   Bu değer genel yönetici adı **olarak adlandırılır**.
7. Kuruluma **Git'i seçin**.
8. Kurulum Office 365 E5,E-posta **ve oturum açma için *onmicrosoft.com'i*** ve sonra Çık ve daha sonra devam **edin'i seçin**.

Aşağıdaki ifadeyi Microsoft 365 yönetim merkezi.
    
## <a name="phase-2-configure-your-office-365-trial-subscription"></a>Aşama 2: Office 365 deneme aboneliğinizi yapılandırma

Bu aşamada, aboneliğinizi başka kullanıcılarla yapılandırıyor ve bu kullanıcılara lisans Office 365 E5 atayabilirsiniz.
  
Bilgisayarınızdan Graph için Azure Active Directory PowerShell modülüyle aboneliğinize bağlanmak için, Bağlan'daki yönergeleri kullanarak [PowerShell Microsoft 365 i deneyin](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
    
Genel **yönetici Windows PowerShell adı** (örneğin, Kimlik Bilgileri İsteği) ve *jdoe@contosotoycompany.onmicrosoft.com* girin.
  
Kuruluş adı girin (örneğin, *contosotoycompany*), konumunuz için iki karakterli ülke kodunu, ortak bir hesap parolasını girin ve PowerShell isteminde aşağıdaki komutları çalıştırın:

```powershell
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$commonPW="<common user account password>"
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPW

$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License

for($i=2;$i -le 4; $i++) {
    $userUPN= "user$($i)@$($orgName).onmicrosoft.com"
    New-AzureADUser -DisplayName "User $($i)" -GivenName User -SurName $i -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user$($i)"
    $userObjectID = (Get-AzureADUser -SearchString $userupn).ObjectID
    Set-AzureADUserLicense -ObjectId $userObjectID -AssignedLicenses $LicensesToAssign
}
```
> [!NOTE]
> Burada sık kullanılan bir parolanın kullanımı, test ortamının otomasyonunu ve yapılandırma kolaylığını sağlar. Bu, üretim abonelikleri için kesinlikle önerilmez. 

### <a name="record-key-information-for-future-reference"></a>Gelecekte başvuru için önemli bilgileri kaydetme

Bu değerleri henüz kaydetmedıysanız, şimdi kaydın:
  
- Genel yönetici adı: ![Satır.](../media/Common-Images/TableLine.png).onmicrosoft.com (Aşama 1'in 6. adımdan itibaren)
    
    Bu hesabın parolasını da güvenli bir konuma yazın.
    
- Deneme aboneliği kuruluş adınız: ![Satır.](../media/Common-Images/TableLine.png) (Aşama 1'in 4. adımından)
    
- Kullanıcı 2, Kullanıcı 3, Kullanıcı 4 ve Kullanıcı 5'in hesaplarını listeleyen kullanıcı isteminde Windows Azure Active Directory Modülü'Windows PowerShell çalıştırın:
    
  ```powershell
  Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    Hesap adlarını buraya kaydetme:
    
  - Kullanıcı 2 hesap adı: kullanıcı2 @![Satır.](../media/Common-Images/TableLine.png).onmicrosoft.com
    
  - Kullanıcı 3 hesap adı: kullanıcı3 @![Satır.](../media/Common-Images/TableLine.png).onmicrosoft.com
    
  - Kullanıcı 4 hesap adı: kullanıcı4 @![Satır.](../media/Common-Images/TableLine.png).onmicrosoft.com
    
  - Kullanıcı 5 hesap adı: kullanıcı5 @![Satır.](../media/Common-Images/TableLine.png).onmicrosoft.com
    
    Ayrıca, bu hesapların ortak parolasını da güvenli bir konuma yazın.
   
### <a name="using-an-office-365-test-environment"></a>Office 365 sınama ortamı kullanma

Yalnızca bir test Office 365 ihtiyacınız varsa, bu makalenin kalan kalanını okumazsınız.

Hem Test Laboratuvarı Kılavuzları hem test hem de test Office 365 Microsoft 365 için Microsoft 365 [Test Laboratuvarı Kılavuzlarına bakın](m365-enterprise-test-lab-guides.md).
  
## <a name="phase-3-add-a-microsoft-365-e5-trial-subscription"></a>Aşama 3: Deneme Microsoft 365 E5 ekleme

Bu aşamada, Microsoft 365 E5 deneme aboneliğine kaydolacak ve bu aboneliği deneme aboneliğiyle aynı Office 365 E5 ekleyebilirsiniz.
  
İlk olarak, Microsoft 365 E5 deneme aboneliğini ekleyin ve yeni Microsoft 365 lisansınızı genel yönetici hesabınıza attayabilirsiniz.
  
1. İnternet tarayıcısının özel penceresinde, genel yönetici hesabı kimlik bilgilerinizi kullanarak tarayıcıda Microsoft 365 yönetim merkezi kullanın[https://admin.microsoft.com](https://admin.microsoft.com).
    
2. Gezinti **Microsoft 365 yönetim merkezi** sol gezinti bölmesinde **BillingPurchase** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=868433" target="_blank">**hizmetleri'ni seçin**</a>.
    
3. Hizmetleri satın **al sayfasında,** Ücretsiz deneme **Microsoft 365 E5'ı** **seçin**.

4. Deneme **Microsoft 365 E5,** kısa mesaj veya telefon görüşmesi almaya karar verin, telefon numaranızı girin ve Ardından Bana kısa mesaj gönder veya Beni  **ara'ya tıklayın**. Doğrulamayı gerçekleştirin.

5. Siparişinizi **onaylayın sayfasında** Şimdi **deneyin'i seçin**.

6. Sipariş alındı **bilgisi sayfasında** Devam'ı **seçin**.

7. Etkin Microsoft 365 yönetim merkezi **Kullanıcılar'ı** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**seçin**</a>.

8. Etkin **kullanıcılar'da** yönetici hesabını seçin.

9. **Lisanslar ve uygulamalar'ı seçin**.

10. E5'te Office 365 Kurumsal devre dışı bırak ve E5 için lisansı Microsoft 365 E5.

11. Değişiklikleri **kaydet'i** seçin ve sonra kullanıcı hesabı bilgileri bölmesini kapatın.

Ardından, önceki yordamın 8 ile 11 arasında olan adımlarını diğer tüm hesaplarınız için tekrarlayın (Kullanıcı 2, Kullanıcı 3, Kullanıcı 4 ve Kullanıcı 5).
  
> [!NOTE]
> Deneme aboneliğinin süresi Microsoft 365 E5 30 gündür. Kalıcı bir test ortamı için, bu deneme aboneliğini az sayıda lisansı olan ücretli bir aboneliğe dönüştürebilirsiniz.
  
Test ortamınız artık şunları sağlar:
  
- Bir Microsoft 365 E5 deneme aboneliği.
- Tüm uygun kullanıcı hesaplarınız (yalnızca genel yönetici veya beş kullanıcı hesabının hepsi) kullanıcı hesaplarının hepsi kullanıcı hesaplarının kullanımına Microsoft 365 E5.
    
Sonuçta elde edilen ve e-Microsoft 365 E5 yapılandırmanız şöyle olur:
  
![Microsoft 3656 test ortamının Enterprise aşaması.](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase2.png)
  
## <a name="phase-4-create-a-windows-10-enterprise-computer"></a>Aşama 4: Windows 10 Enterprise oluşturma

Bu aşamada, fiziksel bilgisayar, Windows 10 Enterprise makine veya Azure sanal makinesi olarak çalışan tek başına bir bilgisayar oluşturmanız gerekir.
  
### <a name="physical-computer"></a>Fiziksel bilgisayar

Kişisel bir bilgisayarda, diğer Windows 10 Enterprise. Windows 10 Enterprise [indirebilirsiniz.](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)
  
### <a name="virtual-machine"></a>Sanal makine

Sanal makine oluşturmak için tercihinizin köprü dizinini kullanın ve sonra makinenizi Windows 10 Enterprise yükleyin. Windows 10 Enterprise [indirebilirsiniz.](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise)
  
### <a name="virtual-machine-in-azure"></a>Azure'da sanal makine

Microsoft Azure'Windows 10 sanal makine oluşturmak ***için, kullanıcı*** Visual Studio resmine erişimi olan Visual Studio tabanlı bir aboneliğiniz Windows 10 Enterprise. Deneme ve ücretli abonelikler gibi diğer Azure abonelik türleri bu görüntüye erişim iznine sahip değildir. En son bilgi için bkz[. Windows/test senaryoları için Azure'da kullanıcı istemcisi kullanma](/azure/virtual-machines/windows/client-images).
  
> [!NOTE]
> Aşağıdaki komut kümeleri, en son Sürüm Azure PowerShell. Bkz[. Yeni cmdlet'leri Azure PowerShell başlama](/powershell/azureps-cmdlets-docs/). Bu komut kümeleri, Windows 10 Enterprise grubu, depolama hesabı ve sanal ağ da içinde olmak üzere WIN10 adlı bir sanal makine ve bunun gerekli tüm altyapısını oluşturmak için kullanılır. Azure altyapı hizmetlerini zaten biliyorsanız, bu yönergeleri şu anda dağıtılan altyapınıza uygun şekilde uyarlayın.
  
İlk olarak, bir Microsoft PowerShell istemini açın.
  
Bu komutla Azure hesabınızla oturum açın.
  
```powershell
Connect-AzAccount
```

Bu komutu kullanarak abonelik adı alın.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

Azure aboneliğinizi ayarlayın. Tırnak işaretleri içindeki her şeyi, karakterlerle birlikte \< and > doğru adla değiştirin.
  
```powershell
$subscr="<subscription name>"
Get-AzSubscription -SubscriptionName $subscr | Select-AzSubscription
```

Ardından, yeni bir kaynak grubu oluşturun. Benzersiz bir kaynak grubu adı belirlemek için, bu komutu kullanarak var olan kaynak gruplarınızı listelenin.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Bu komutlarla yeni kaynak grubunızı oluşturun. Tırnak içindeki her şeyi, karakterlerle birlikte \< and > doğru adlarla değiştirin.
  
```powershell
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzResourceGroup -Name $rgName -Location $locName
```

Ardından, bu komutlarla yeni bir sanal ağ ve WIN10 sanal makinesi oluşturun. Sorulsa, WIN10 için yerel yönetici hesabının adını ve parolasını girin ve bunları güvenli bir yerde depo edin.
  
```powershell
$corpnetSubnet=New-AzVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzVirtualNetwork -Name "M365Ent-TestLab" -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name "M365Ent-TestLab"
$nsg=Get-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
$pip=New-AzPublicIpAddress -Name WIN10-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name WIN10-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzVMConfig -VMName WIN10 -VMSize Standard_A2_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for WIN10."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName WIN10 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsDesktop -Offer Windows-10 -Skus RS3-Pro -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name WIN10-TestLab-OSDisk -DiskSizeInGB 128 -CreateOption FromImage
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

## <a name="phase-5-join-your-windows-10-computer-to-azure-ad"></a>Aşama 5: Bilgisayarınızdan Azure AD Windows 10 e katılma

Oturum açma hesabı olan fiziksel Windows 10 Enterprise sanal makine oluşturulduktan sonra, yerel yönetici hesabıyla oturum açın.
  
> [!NOTE]
> Azure'daki bir sanal makineye  [bağlanmak için](/azure/virtual-machines/windows/connect-logon) bu yönergeleri kullanın.
  
Daha sonra, Microsoft 365 E5 aboneliğinizin Azure AD kiracısına WIN10 bilgisayarına katılın.
  
1. WIN10 bilgisayarının masaüstünde, İş veya okul hesabınıza **erişmek > Ayarlar > Hesapları >'ı > Bağlan**.
    
2. İş **veya okul hesabı ayarla iletişim kutusunda Bu** cihaza **katıl'ı seçerek bu Azure Active Directory**.
    
3. İş **veya okul hesabı alanına**, okul aboneliğinizin genel yönetici hesabı Microsoft 365 E5 ve sonra Da Sonra'ya **tıklayın**.
    
4. **Parolayı girin** alanına, genel yönetici hesabınız için parolayı girin ve Oturum **açın'ı seçin**.
    
5. Bunun sizin kuruluşta olduğundan emin olmak istendiğinde Katıl'ı **ve ardından** Bitti'yi **seçin**.
    
6. Ayarlar penceresini kapatın.
    
Ardından WIN10 Kurumlar için Microsoft 365 Uygulamaları yükleme:
  
1. Microsoft Edge tarayıcısını açın ve genel yönetici [Microsoft 365 yönetim merkezi kimlik](https://admin.microsoft.com) bilgilerinizle oturum açın.
    
2. Sayfa Giriş **Microsoft Office Yükleme'yi** **seçin ve sonra da Office**.
    
3. Ne yapmak istediğiniz sorulsa, **Çalıştır'ı ve** sonra Kullanıcı Hesabı Denetimi **için** **Evet'i seçin**.
    
4. Yüklemenin Office için bekleyin. Hazır olduğunu **gördüğünüzde, Kapat'ı** iki **kez** seçin.
    
Sonuçta elde edilen ortamınız şöyle görünüyor:

![Microsoft 3656 test ortamının Enterprise aşaması.](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase4.png)

Bu, aşağıdakilerin olduğu WIN10 bilgisayarlarını içerir:

- Microsoft 365 E5 aboneliğinizin Azure AD kiracısına katıldı.
- Microsoft Intune'de (EMS) Azure AD cihazı olarak kaydoldu.
- Kurumlar için Microsoft 365 Uygulamaları yüklü.
  
Artık kurumsal kullanıma uygun uygulamanın ek özelliklerini [Microsoft 365 hazır mısınız](https://www.microsoft.com/microsoft-365/enterprise)?
  
## <a name="next-steps"></a>Sonraki adımlar

Bu ek Test Laboratuvarı Kılavuzlarını keşfedin:
  
- [Kimlik](m365-enterprise-test-lab-guides.md#identity)
- [Mobil cihaz yönetimi](m365-enterprise-test-lab-guides.md#mobile-device-management)
- [Bilgi koruması](m365-enterprise-test-lab-guides.md#information-protection)
   

## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 Test Laboratuvarı Kılavuzları için kılavuzlar](m365-enterprise-test-lab-guides.md)

[Microsoft 365 genel bakış için genel bakış](microsoft-365-overview.md)

[Microsoft 365 belgeleri için belgeler](/microsoft-365-enterprise/)
