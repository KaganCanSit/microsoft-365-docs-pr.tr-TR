---
title: Microsoft 365 test ortamınız için federasyon kimliği
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 05/26/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 65a6d687-a16a-4415-9fd5-011ba9c5fd80
description: 'Özet: Microsoft 365 test ortamınız için federasyon kimlik doğrulamasını yapılandırın.'
ms.openlocfilehash: 0214c7778176641c6446106cf92ed173b81b71de
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101039"
---
# <a name="federated-identity-for-your-microsoft-365-test-environment"></a>Microsoft 365 test ortamınız için federasyon kimliği

*Bu Test Laboratuvarı Kılavuzu hem kurumsal hem de Office 365 Kurumsal test ortamları için Microsoft 365 için kullanılabilir.*

Microsoft 365 federasyon kimliğini destekler. Bu, kimlik bilgilerinin doğrulanması yerine Microsoft 365 bağlanan kullanıcıyı güvenen bir federasyon kimlik doğrulama sunucusuna Microsoft 365 anlamına gelir. Kullanıcının kimlik bilgileri doğruysa, federasyon kimlik doğrulama sunucusu istemcinin kimlik doğrulaması kanıtı olarak Microsoft 365 gönderdiği bir güvenlik belirteci verir. Federasyon kimliği, Microsoft 365 aboneliği ve gelişmiş kimlik doğrulaması ve güvenlik senaryoları için kimlik doğrulamasının boşaltılmasını ve ölçeklendirilmesini sağlar.
  
Bu makalede, Microsoft 365 test ortamınız için federasyon kimlik doğrulamasının nasıl yapılandırıldığı açıklanır ve sonuç olarak aşağıdakiler elde edilir:

![Microsoft 365 test ortamı için federasyon kimlik doğrulaması.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase3.png)
  
Bu yapılandırma şunlardan oluşur:
  
- Microsoft 365 E5 deneme veya üretim aboneliği.
    
- Azure sanal ağının alt ağındaki beş sanal makineden (DC1, APP1, CLIENT1, ADFS1 ve PROXY1) oluşan, internete bağlı basitleştirilmiş bir kuruluş intraneti. Azure AD Bağlan, Active Directory Domain Services etki alanındaki hesap listesini Microsoft 365 eşitlemek için APP1 üzerinde çalışır. PROXY1 gelen kimlik doğrulama isteklerini alır. ADFS1, DC1 ile kimlik bilgilerini doğrular ve güvenlik belirteçleri verir.
    
Bu test ortamının ayarlanması beş aşamadan oluşur:
- [1. Aşama: Microsoft 365 test ortamınız için parola karması eşitlemesini yapılandırma](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [2. Aşama: AD FS sunucusunu oluşturma](#phase-2-create-the-ad-fs-server)
- [3. Aşama: Web proxy sunucusunu oluşturma](#phase-3-create-the-web-proxy-server)
- [4. Aşama: Otomatik olarak imzalanan bir sertifika oluşturma ve ADFS1 ile PROXY1'i yapılandırma](#phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1)
- [5. Aşama: Federasyon kimliği için Microsoft 365 yapılandırma](#phase-5-configure-microsoft-365-for-federated-identity)
    
> [!NOTE]
> Bu test ortamını azure deneme aboneliğiyle yapılandıramazsınız.
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>1. Aşama: Microsoft 365 test ortamınız için parola karması eşitlemesini yapılandırma

[Microsoft 365 için parola karması eşitlemesindeki](password-hash-sync-m365-ent-test-environment.md) yönergeleri izleyin. Sonuçta elde edilen yapılandırmanız şöyle görünür:
  
![Parola karması eşitleme testi ortamı ile sanal kuruluş.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase1.png)
  
Bu yapılandırma şunlardan oluşur:
  
- Microsoft 365 E5 deneme sürümü veya ücretli abonelikler.
- Azure sanal ağının alt ağındaki DC1, APP1 ve CLIENT1 sanal makinelerinden oluşan, internete bağlı basitleştirilmiş bir kuruluş intraneti. Azure AD Bağlan, TESTLAB Active Directory Domain Services (AD DS) etki alanını düzenli aralıklarla Microsoft 365 aboneliklerinizin Azure AD kiracısıyla eşitlemek için APP1 üzerinde çalışır.

## <a name="phase-2-create-the-ad-fs-server"></a>2. Aşama: AD FS sunucusunu oluşturma

AD FS sunucusu, Microsoft 365 ile DC1'de barındırılan corp.contoso.com etki alanındaki hesaplar arasında federasyon kimlik doğrulaması sağlar.
  
ADFS1 için bir Azure sanal makinesi oluşturmak için aboneliğinizin adını, kaynak grubunu ve Temel Yapılandırmanızın Azure konumunu girin ve ardından bu komutları yerel bilgisayarınızdaki Azure PowerShell komut isteminde çalıştırın.
  
```powershell
$subscrName="<your Azure subscription name>"
$rgName="<the resource group name of your Base Configuration>"
$vnetName="TlgBaseConfig-01-VNET"
# NOTE: If you built your simulated intranet with Azure PowerShell, comment the previous line with a "#" and remove the "#" from the next line.
#$vnetName="TestLab"
Connect-AzAccount
Select-AzSubscription -SubscriptionName $subscrName
$staticIP="10.0.0.100"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$pip = New-AzPublicIpAddress -Name ADFS1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic = New-AzNetworkInterface -Name ADFS1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName ADFS1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for ADFS1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName ADFS1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "ADFS-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Ardından[, ADFS1](https://portal.azure.com) yerel yönetici hesabı adını ve parolasını kullanarak ADFS1 sanal makinesine bağlanmak için Azure portal kullanın ve ardından bir Windows PowerShell komut istemi açın.
  
ADFS1 ile DC1 arasındaki ad çözümlemesini ve ağ iletişimini denetlemek için **ping dc1.corp.contoso.com** komutunu çalıştırın ve dört yanıt olup olmadığını denetleyin.
  
Ardından, ADFS1'deki Windows PowerShell isteminde bu komutlarla ADFS1 sanal makinesini CORP etki alanına ekleyin.
  
```powershell
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

Sonuçta elde edilen yapılandırmanız şöyle görünür:
  
![AD FS sunucusu, Microsoft 365 test ortamı için DirSync'e eklendi.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase2.png)
  
## <a name="phase-3-create-the-web-proxy-server"></a>3. Aşama: Web proxy sunucusunu oluşturma

PROXY1, kimlik doğrulaması yapmaya çalışan kullanıcılar ile ADFS1 arasında kimlik doğrulama iletilerinin ara sunucusu sağlar.
  
PROXY1 için bir Azure sanal makinesi oluşturmak için kaynak grubunuzun adını ve Azure konumunu girin ve ardından bu komutları yerel bilgisayarınızdaki Azure PowerShell komut isteminde çalıştırın.
  
```powershell
$rgName="<the resource group name of your Base Configuration>"
$vnetName="TlgBaseConfig-01-VNET"
# NOTE: If you built your simulated intranet with Azure PowerShell, comment the previous line with a "#" and remove the "#" from the next line.
#$vnetName="TestLab"
$staticIP="10.0.0.101"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$pip = New-AzPublicIpAddress -Name PROXY1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Static
$nic = New-AzNetworkInterface -Name PROXY1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName PROXY1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for PROXY1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName PROXY1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "PROXY1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> PROXY1'e statik bir genel IP adresi atanır çünkü buna işaret eden bir genel DNS kaydı oluşturursunuz ve PROXY1 sanal makinesini yeniden başlattığınızda bu kayıt değişmemelidir.
  
Ardından, İnternet'ten PROXY1'in özel IP adresine ve TCP bağlantı noktası 443'e istenmeyen gelen trafiğe izin vermek için CorpNet alt ağının ağ güvenlik grubuna bir kural ekleyin. Bu komutları yerel bilgisayarınızdaki Azure PowerShell komut isteminde çalıştırın.
  
```powershell
$rgName="<the resource group name of your Base Configuration>"
Get-AzNetworkSecurityGroup -Name CorpNet -ResourceGroupName $rgName | Add-AzNetworkSecurityRuleConfig -Name "HTTPS-to-PROXY1" -Description "Allow TCP 443 to PROXY1" -Access "Allow" -Protocol "Tcp" -Direction "Inbound" -Priority 101 -SourceAddressPrefix "Internet" -SourcePortRange "*" -DestinationAddressPrefix "10.0.0.101" -DestinationPortRange "443" | Set-AzNetworkSecurityGroup
```

Ardından[, proxy1](https://portal.azure.com) yerel yönetici hesabı adını ve parolasını kullanarak PROXY1 sanal makinesine bağlanmak için Azure portal kullanın ve ardından PROXY1'de bir Windows PowerShell komut istemi açın.
  
PROXY1 ile DC1 arasındaki ad çözümlemesini ve ağ iletişimini denetlemek için **ping dc1.corp.contoso.com** komutunu çalıştırın ve dört yanıt olup olmadığını denetleyin.
  
Ardından, PROXY1'deki Windows PowerShell isteminde bu komutlarla PROXY1 sanal makinesini CORP etki alanına ekleyin.
  
```powershell
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

Yerel bilgisayarınızda bu Azure PowerShell komutlarıyla PROXY1'in genel IP adresini görüntüleyin.
  
```powershell
Write-Host (Get-AzPublicIpaddress -Name "PROXY1-PIP" -ResourceGroup $rgName).IPAddress
```

Ardından, genel DNS sağlayıcınızla çalışın ve **fs.testlab** için yeni bir genel DNS A kaydı oluşturun.\<*your DNS domain name*> bu, **Write-Host** komutu tarafından görüntülenen IP adresine çözümleniyor. **fs.testlab.**\<*your DNS domain name*> bundan sonra  *federasyon hizmeti FQDN* olarak adlandırılır.
  
Ardından[, CORPUser1](https://portal.azure.com)\\ kimlik bilgilerini kullanarak DC1 sanal makinesine bağlanmak için Azure portal kullanın ve ardından yönetici düzeyinde Windows PowerShell komut isteminde aşağıdaki komutları çalıştırın:
  
```powershell
Add-DnsServerPrimaryZone -Name corp.contoso.com -ZoneFile corp.contoso.com.dns
Add-DnsServerResourceRecordA -Name "fs" -ZoneName corp.contoso.com -AllowUpdateAny -IPv4Address "10.0.0.100" -TimeToLive 01:00:00
```
Bu komutlar, Azure sanal ağındaki sanal makinelerin iç federasyon hizmeti FQDN'sini ADFS1'in özel IP adresine çözümleyebilmesi için bir iç DNS A kaydı oluşturur.
  
Sonuçta elde edilen yapılandırmanız şöyle görünür:
  
![Microsoft 365 test ortamı için DirSync'e eklenen web uygulaması proxy sunucusu.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase3.png)
  
## <a name="phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1"></a>4. Aşama: Otomatik olarak imzalanan bir sertifika oluşturma ve ADFS1 ile PROXY1'i yapılandırma

Bu aşamada, federasyon hizmeti FQDN'niz için otomatik olarak imzalanan bir dijital sertifika oluşturur ve ADFS1 ile PROXY1'i bir AD FS grubu olarak yapılandırabilirsiniz.
  
İlk olarak, CORPUser1\\ kimlik bilgilerini kullanarak DC1 sanal makinesine bağlanmak için [Azure portal](https://portal.azure.com) kullanın ve ardından yönetici düzeyinde bir Windows PowerShell komut istemi açın.
  
Ardından, DC1'deki Windows PowerShell komut isteminde şu komutla bir AD FS hizmet hesabı oluşturun:
  
```powershell
New-ADUser -SamAccountName ADFS-Service -AccountPassword (read-host "Set user password" -assecurestring) -name "ADFS-Service" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```
Bu komutun sizden hesap parolasını girmenizi istediğini unutmayın. Güçlü bir parola seçin ve güvenli bir konuma kaydedin. Bu aşama ve 5. Aşama için buna ihtiyacınız olacaktır.
  
CORPUser1\\ kimlik bilgilerini kullanarak ADFS1 sanal makinesine bağlanmak için [Azure portal](https://portal.azure.com) kullanın. ADFS1'de yönetici düzeyinde bir Windows PowerShell komut istemi açın, federasyon hizmeti FQDN'nizi doldurun ve otomatik olarak imzalanan bir sertifika oluşturmak için şu komutları çalıştırın:
  
```powershell
$fedServiceFQDN="<federation service FQDN>"
New-SelfSignedCertificate -DnsName $fedServiceFQDN -CertStoreLocation "cert:\LocalMachine\My"
New-Item -path c:\Certs -type directory
New-SmbShare -name Certs -path c:\Certs -changeaccess CORP\User1
```

Ardından, yeni otomatik olarak imzalanan sertifikayı dosya olarak kaydetmek için bu adımları kullanın.
  
1. **Başlat'ı** seçin, **mmc.exe** yazın ve **Enter tuşuna** basın.
    
2. **Ek** >  **Bileşen Ekle/Kaldır'ı** seçin.
    
3. **Ek Bileşen Ekle veya Kaldır'da**, kullanılabilir ek bileşenler listesinde **Sertifikalar'a** çift tıklayın, **Bilgisayar hesabı'nı** ve ardından **İleri'yi** seçin.
    
4. **Bilgisayar Seç'te** **Son'u** ve ardından **Tamam'ı** seçin.
    
5. Ağaç bölmesinde Kişisel **> Sertifikaları > Sertifikalar (Yerel Bilgisayar)** öğesini açın.
    
6. Federasyon hizmeti FQDN'nizin olduğu sertifikayı seçip basılı tutun (veya sağ tıklayın), **Tüm görevler'i** ve ardından **Dışarı Aktar'ı** seçin.
    
7. **Hoş Geldiniz** sayfasında **İleri'yi** seçin.
    
8. **Özel Anahtarı Dışarı Aktar** sayfasında **Evet'i** ve ardından **İleri'yi** seçin.
    
9. **Dosya Biçimini Dışarı Aktar** sayfasında **Tüm genişletilmiş özellikleri dışarı aktar'ı** ve ardından **İleri'yi** seçin.
    
10. **Güvenlik** sayfasında **Parola'yı** seçin ve Parola **ve** **Parolayı onayla'ya bir parola girin.**
    
11. **Dışarı Aktaracak Dosya** sayfasında **Gözat'ı** seçin.
    
12. **C:\\Certs** klasörüne gidin, **Dosya adı** alanına **SSL** girin ve **Kaydet'i seçin.**
    
13. **Dışarı Aktaracak Dosya** sayfasında **İleri'yi** seçin.
    
14. **Sertifika Dışarı Aktarma Sihirbazı Tamamlanıyor** sayfasında **Son'u** seçin. İstendiğinde **Tamam'ı** seçin.
    
Ardından, AD FS hizmetini ADFS1'deki Windows PowerShell komut isteminde şu komutla yükleyin:
  
```powershell
Install-WindowsFeature ADFS-Federation -IncludeManagementTools
```

Yüklemenin tamamlanmasını bekleyin.
  
Ardından, AD FS hizmetini şu adımlarla yapılandırın:
  
1. **Başlat'ı** ve ardından **Sunucu Yöneticisi** simgesini seçin.
    
2. Sunucu Yöneticisi ağaç bölmesinde **AD FS'yi** seçin.
    
3. Üstteki araç çubuğunda turuncu uyarı simgesini seçin ve ardından **Bu sunucuda federasyon hizmetini yapılandır'ı** seçin.
    
4. Active Directory Federasyon Hizmetleri (AD FS) Yapılandırma Sihirbazı'nın **Hoş Geldiniz** sayfasında **İleri'yi** seçin.
    
5. **AD DS'ye Bağlan** sayfasında **İleri'yi** seçin.
    
6. **Hizmet Özelliklerini Belirt** sayfasında:
    
  - **SSL Sertifikası** için aşağı oku ve ardından federasyon hizmeti FQDN'nizin adını içeren sertifikayı seçin.
    
  - **Federasyon Hizmeti Görünen Adı** alanına kurgusal kuruluşunuzun adını girin.
    
  - **İleri**'yi seçin.
    
7. **Hizmet Hesabını Belirtin** sayfasında **Hesap adı** için **Seç'i** seçin.
    
8. **Kullanıcı veya Hizmet Hesabı Seç'e** **ADFS-Service** girin, **Adları Denetle'yi** ve ardından **Tamam'ı** seçin.
    
9. **Hesap Parolası'nda**, ADFS-Service hesabının parolasını girin ve **İleri'yi** seçin.
    
10. **Yapılandırma Veritabanını Belirtin** sayfasında **İleri'yi** seçin.
    
11. **Gözden Geçirme Seçenekleri** sayfasında **İleri'yi** seçin.
    
12. **Önkoşul Denetimleri** sayfasında **Yapılandır'ı** seçin.

13. **Sonuçlar** sayfasında **Kapat'ı** seçin.
    
14. **Başlat'ı** seçin, güç simgesini seçin, **Yeniden Başlat'ı** ve ardından **Devam'ı** seçin.
    
[Azure portal](https://portal.azure.com), CORPUser1\\ hesabı kimlik bilgileriyle PROXY1'e bağlanın.
  
Ardından, otomatik olarak imzalanan sertifikayı **hem PROXY1'e hem de APP1'e** yüklemek için bu adımları kullanın.
  
1. **Başlat'ı** seçin, **mmc.exe** yazın ve **Enter tuşuna** basın.
    
2. **Dosya > Ek Bileşen Ekle/Kaldır'ı** seçin.
    
3. **Ek Bileşen Ekle veya Kaldır'da**, kullanılabilir ek bileşenler listesinde **Sertifikalar'a** çift tıklayın, **Bilgisayar hesabı'nı** ve ardından **İleri'yi** seçin.
    
4. **Bilgisayar Seç'te** **Son'u** ve ardından **Tamam'ı** seçin.
    
5. Ağaç bölmesinde **Sertifikalar (Yerel Bilgisayar)** > **KişiselSertifikalar'ı** >  açın.
    
6. **Kişisel'i** seçip basılı tutun (veya sağ tıklayın), **Tüm görevler'i** ve ardından **İçeri Aktar'ı** seçin.
    
7. **Hoş Geldiniz** sayfasında **İleri'yi** seçin.
    
8. **İçeri Aktaracak Dosya** sayfasında **adfs1certsssl.pfx\\\\ girin\\\\** ve **İleri'yi** seçin.
    
9. **Özel anahtar koruması** sayfasında **Parola alanına sertifika** parolasını girin ve **İleri'yi seçin.**
    
10. **Sertifika deposu** sayfasında **İleri'yi seçin.**
    
11. **Tamamlanıyor** sayfasında **Son'u** seçin.
    
12. **Sertifika Deposu** sayfasında **İleri'yi** seçin.
    
13. İstendiğinde **Tamam'ı** seçin.
    
14. Ağaç bölmesinde **Sertifikalar'ı** seçin.
    
15. Sertifikayı seçip basılı tutun (veya sağ tıklayın) ve ardından **Kopyala'yı** seçin.
    
16. Ağaç bölmesinde **Güvenilen Kök Sertifika** **YetkilileriCertificates'i** >  açın.
    
17. Fare işaretçinizi yüklü sertifikalar listesinin altına getirin, seçip basılı tutun (veya sağ tıklayın) ve ardından **Yapıştır'ı** seçin.
    
Yönetici düzeyinde bir PowerShell komut istemi açın ve aşağıdaki komutu çalıştırın:
  
```powershell
Install-WindowsFeature Web-Application-Proxy -IncludeManagementTools
```

Yüklemenin tamamlanmasını bekleyin.
  
Web uygulaması proxy hizmetini ADFS1'i federasyon sunucusu olarak kullanacak şekilde yapılandırmak için şu adımları kullanın:
  
1. **Başlat'ı** ve ardından **Sunucu Yöneticisi'ı** seçin.
    
2. Ağaç bölmesinde **Uzaktan Erişim'i** seçin.
    
3. Üstteki araç çubuğunda turuncu uyarı simgesini ve ardından **Web Uygulama Ara Sunucusu Sihirbazını Aç'ı** seçin.
    
4. Web Uygulama Ara Sunucusu Yapılandırma Sihirbazı'nın **Hoş Geldiniz** sayfasında **İleri'yi** seçin.
    
5. **Federasyon Sunucusu** sayfasında:
    
  - **Federasyon hizmeti adı** kutusuna federasyon hizmeti FQDN'nizi girin.
    
  - **Kullanıcı adı** kutusuna **CORPUser1\\** yazın.
    
  - **Parola** kutusuna User1 hesabının parolasını girin.
    
  - **İleri**'yi seçin.
    
6. **AD FS Proxy Sertifikası** sayfasında aşağı oku seçin, federasyon hizmeti FQDN'nizin olduğu sertifikayı seçin ve ardından **İleri'yi** seçin.
    
7. **Onay** sayfasında **Yapılandır'ı** seçin.
    
8. **Sonuçlar** sayfasında **Kapat'ı** seçin.
    
## <a name="phase-5-configure-microsoft-365-for-federated-identity"></a>5. Aşama: Federasyon kimliği için Microsoft 365 yapılandırma

CORPUser1\\ hesabı kimlik bilgileriyle APP1 sanal makinesine bağlanmak için [Azure portal](https://portal.azure.com) kullanın.
  
Azure AD Bağlan ve Microsoft 365 aboneliğinizi federasyon kimlik doğrulaması için yapılandırmak için şu adımları kullanın:
  
1. Masaüstünden **Azure AD Bağlan'ne** çift tıklayın.
    
2. **Azure AD'ye Hoş Geldiniz Bağlan** sayfasında **Yapılandır'ı** seçin.
    
3. **Ek görevler** sayfasında **Kullanıcı oturumunu değiştir'i ve ardından İleri'yi** seçin.
    
4. **Azure AD'ye Bağlan** sayfasında genel yönetici hesabınızın adını ve parolasını girin ve **İleri'yi** seçin.
    
5. **Kullanıcı oturum açma** sayfasında **AD FS ile Federasyon'a** ve ardından **İleri'ye** tıklayın.
    
6. **AD FS grubu** sayfasında **Var olan bir AD FS grubu kullan'ı** seçin, **Sunucu Adı** kutusuna **ADFS1** yazın ve **İleri'yi** seçin.
    
7. Sunucu kimlik bilgileri istendiğinde CORPUser1 hesabının kimlik bilgilerini\\ girin ve **Tamam'ı** seçin.
    
8. **Etki Alanı Yöneticisi** kimlik bilgileri sayfasında, **Kullanıcı adı** kutusuna **CORPUser1\\** yazın, **Parola** kutusuna hesap parolasını girin ve **İleri'yi** seçin.
    
9. **AD FS hizmet hesabı** sayfasında, **Etki Alanı Kullanıcı Adı** kutusuna **CORPADFS-Service\\** yazın, **Etki Alanı Kullanıcı Parolası** kutusuna hesap parolasını girin ve **İleri'yi** seçin.
    
10. **Azure AD Etki Alanı** sayfasındaki **Etki Alanı'nda**, daha önce oluşturduğunuz ve 1. Aşamada aboneliğinize eklediğiniz etki alanının adını seçin ve ardından **İleri'yi** seçin.
    
11. **Yapılandırmaya hazır** sayfasında **Yapılandır'ı** seçin.
    
12. **Yükleme tamamlandı** sayfasında **Doğrula'yı** seçin.
    
    Hem intranet hem de internet yapılandırmasının doğrulandığını belirten iletiler görmeniz gerekir.
    
13. **Yükleme tamamlandı** sayfasında **Çıkış'ı** seçin.
    
Federasyon kimlik doğrulamasının çalıştığını göstermek için:
  
1. Yerel bilgisayarınızda tarayıcınızın yeni bir özel örneğini açın ve adresine [https://admin.microsoft.com](https://admin.microsoft.com)gidin.
    
2. Oturum açma kimlik bilgileri için **user1@**\<*the domain created in Phase 1*> girin.
    
    Örneğin, test etki alanınız **testlab.contoso.com** ise "user1@testlab.contoso.com" girersiniz. **Sekme** tuşuna basın veya Microsoft 365 sizi otomatik olarak yeniden yönlendirmesine izin verin.
    
    Şimdi **Bağlantınız özel değil** sayfasını görmeniz gerekir. Bunun nedeni, masaüstü bilgisayarınızın doğrulanamadığından ADFS1'e otomatik olarak imzalanan bir sertifika yüklemiş olmanızdır. Federasyon kimlik doğrulamasının üretim dağıtımında, güvenilen bir sertifika yetkilisinden bir sertifika kullanırsınız ve kullanıcılarınız bu sayfayı görmez.
    
3. **Bağlantınız özel değil** sayfasında **Gelişmiş'i** ve ardından **devam et'i \<*your federation service FQDN*>** seçin. 
    
4. Kurgusal kuruluşunuzun adını içeren sayfada aşağıdakilerle oturum açın:
    
  - **CORP\\ Ad için Kullanıcı1**
    
  - User1 hesabının parolası
    
    **Microsoft Office Giriş** sayfasını görmeniz gerekir.
    
Bu yordam, deneme aboneliğinizin DC1'de barındırılan AD DS corp.contoso.com etki alanıyla birleştirilmiş olduğunu gösterir. Kimlik doğrulama işleminin temelleri şunlardır:
  
1. Oturum açma hesabı adı içinde 1. Aşamada oluşturduğunuz federasyon etki alanını kullandığınızda, Microsoft 365 tarayıcınızı federasyon hizmeti FQDN'nize ve PROXY1'inize yönlendirir.
    
2. PROXY1, yerel bilgisayarınıza kurgusal şirket oturum açma sayfasını gönderir.
    
3. CORPUser1\\ ve parolayı PROXY1'e gönderdiğinizde, bunları ADFS1'e iletir.
    
4. ADFS1, CORPUser1\\ ve parolayı DC1 ile doğrular ve yerel bilgisayarınıza bir güvenlik belirteci gönderir.
    
5. Yerel bilgisayarınız güvenlik belirtecini Microsoft 365 gönderir.
    
6. Microsoft 365, güvenlik belirtecinin ADFS1 tarafından oluşturulduğunu doğrular ve erişime izin verir.
    
Deneme aboneliğiniz artık federasyon kimlik doğrulamasıyla yapılandırıldı. Gelişmiş kimlik doğrulama senaryoları için bu geliştirme/test ortamını kullanabilirsiniz.
  
## <a name="next-step"></a>Sonraki adım

Azure'da Microsoft 365 için üretime hazır, yüksek kullanılabilirliğe yönelik federasyon kimlik doğrulamasını dağıtmaya hazır olduğunuzda bkz. [Azure'da Microsoft 365 için yüksek kullanılabilirlikli federasyon kimlik doğrulaması dağıtma](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md).
  
