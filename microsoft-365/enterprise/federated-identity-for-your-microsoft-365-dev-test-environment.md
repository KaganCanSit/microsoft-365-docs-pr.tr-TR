---
title: Test ortamınız için Microsoft 365 kimlik
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'Özet: Test ortamınız için federasyon kimlik Microsoft 365 yapılandırma.'
ms.openlocfilehash: 6553590c06df4caf099c7b4db47d253bd37b39fd
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983504"
---
# <a name="federated-identity-for-your-microsoft-365-test-environment"></a>Test ortamınız için Microsoft 365 kimlik

*Bu Test Laboratuvarı Kılavuzu, hem kurumsal hem de Microsoft 365 test ortamları için Office 365 Kurumsal kullanılabilir.*

Microsoft 365 kimlikleri destekler. Bu, kimlik bilgilerinin kendi doğrulamasını yapmak yerine, Microsoft 365 kullanıcının güvenlerini sağlayan bir federasyon kimlik doğrulama sunucusuna Microsoft 365 anlamına gelir. Kullanıcının kimlik bilgileri doğruysa, federasyon kimlik doğrulama sunucusu, istemcinin kimlik doğrulama kanıtı olarak Microsoft 365'e gönderdiği bir güvenlik belirteci gönderir. Federasyon kimliği, bir kurumsal abonelik ve gelişmiş kimlik doğrulama ve güvenlik senaryoları için kimlik Microsoft 365 ve ölçeklendirmeye olanak sağlar.
  
Bu makalede, test ortamınız için federasyon kimlik doğrulamasının nasıl Microsoft 365 ve bunun sonucunda aşağıdakiler ortaya konur:

![Test ortamı için federasyon Microsoft 365 doğrulama.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase3.png)
  
Bu yapılandırma şunları oluşur:
  
- Deneme Microsoft 365 E5 üretim aboneliği.
    
- Azure sanal ağının (DC1, APP1, CLIENT1, ADFS1 ve PROXY1) alt ağına beş sanal makineden oluşan, İnternet'e bağlı basitleştirilmiş bir kuruluş intraneti. Azure AD Bağlan Active Directory Etki Alanı Hizmetleri etki alanındaki hesap listesini eşitlemek için APP1'te Microsoft 365. PROXY1 gelen kimlik doğrulama isteklerini alır. ADFS1, kimlik bilgilerini DC1 ile doğrular ve güvenlik belirteçleriyle ilgili sorunları doğrular.
    
Bu test ortamını ayarlama beş aşama içerir:
- [Aşama 1: Test ortamınız için parola Microsoft 365 eşitlemesini yapılandırma](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [Aşama 2: AD FS sunucusunu oluşturma](#phase-2-create-the-ad-fs-server)
- [Aşama 3: Web ara sunucusu oluşturma](#phase-3-create-the-web-proxy-server)
- [Aşama 4: Otomatik olarak imzalanan sertifika oluşturma ve ADFS1 ve PROXY1'i yapılandırma](#phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1)
- [Aşama 5: Federasyon Microsoft 365 yapılandırma](#phase-5-configure-microsoft-365-for-federated-identity)
    
> [!NOTE]
> Azure Deneme aboneliğiyle bu test ortamını yapılandıramazsanız.
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Aşama 1: Test ortamınız için parola Microsoft 365 eşitlemesini yapılandırma

Karma parola [eşitlemesi için verilen yönergeleri Microsoft 365](password-hash-sync-m365-ent-test-environment.md). Sonuçta elde edilen yapılandırmanız şöyle görünüyor:
  
![Parola karma eşitlemesi test ortamına sahip sanal kuruluş.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase1.png)
  
Bu yapılandırma şunları oluşur:
  
- Deneme Microsoft 365 E5 ücretli abonelikler.
- İnternet'e bağlı, Azure sanal ağının alt ağına DC1, APP1 ve CLIENT1 sanal makinelerinden oluşan basitleştirilmiş bir kuruluş intraneti. Azure AD Bağlan, TESTLAB Active Directory Etki Alanı Hizmetleri (AD DS) etki alanını düzenli aralıklarla Microsoft 365 aboneliklerinizin Azure AD kiracısına eşitlemek için APP1'de çalışır.

## <a name="phase-2-create-the-ad-fs-server"></a>Aşama 2: AD FS sunucusunu oluşturma

AD FS sunucusu, DC1 Microsoft 365 te barındırılan etki corp.contoso.com hesaplar arasında federasyon kimlik doğrulaması sağlar.
  
ADFS1 için bir Azure sanal makinesi oluşturmak için, aboneliğinizin adını, Temel Yapılandırmanız için kaynak grubunun ve Azure konumunu doldurun ve ardından bu komutları yerel Azure PowerShell Komut İstemi'nde çalıştırın.
  
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

Ardından, ADFS1 yerel yönetici hesap adı ve parolasını kullanarak ADFS1 sanal makinesine bağlanmak için [Azure portalını](https://portal.azure.com) kullanın ve ardından Windows PowerShell istemini açın.
  
Ad çözümlemesi ile ADFS1 ile DC1 arasındaki ağ iletişimini kontrol etmek için **, ping dc1.corp.contoso.com** çalıştırarak dört yanıt olduğunu kontrol edin.
  
Ardından, ADFS1'de Komut isteminde bu komutları kullanarak ADFS1 sanal Windows PowerShell CORP etki alanına katılın.
  
```powershell
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

Sonuçta elde edilen yapılandırmanız şöyle görünüyor:
  
![Test ortamı için DirSync'e eklenen AD FS Microsoft 365 ortamı.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase2.png)
  
## <a name="phase-3-create-the-web-proxy-server"></a>Aşama 3: Web ara sunucusu oluşturma

PROXY1, kimlik doğrulamaya çalışan kullanıcılar ile ADFS1 arasındaki kimlik doğrulama iletilerinin ara sunucularını sağlar.
  
PROXY1 için bir Azure sanal makinesi oluşturmak için, kaynak grubu ve Azure konumunun adını doldurun ve ardından bu komutları yerel bilgisayarınızda Azure PowerShell komut isteminde çalıştırın.
  
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
> PROXY1'e statik genel IP adresi atanır, çünkü bu adresin olduğu bir genel DNS kaydı oluşturacağız ve PROXY1 sanal makinesi yeniden başlatıldığında bu kayıt değişmez.
  
Ardından, Proxy1'in özel IP adresine ve TCP bağlantı noktası 443'e internetten gelen istenmeyen trafike izin vermek için CorpNet alt ağına yönelik ağ güvenlik grubuna bir kural ekleyin. Bu komutları yerel Azure PowerShell Komut İstemi'nde çalıştırın.
  
```powershell
$rgName="<the resource group name of your Base Configuration>"
Get-AzNetworkSecurityGroup -Name CorpNet -ResourceGroupName $rgName | Add-AzNetworkSecurityRuleConfig -Name "HTTPS-to-PROXY1" -Description "Allow TCP 443 to PROXY1" -Access "Allow" -Protocol "Tcp" -Direction "Inbound" -Priority 101 -SourceAddressPrefix "Internet" -SourcePortRange "*" -DestinationAddressPrefix "10.0.0.101" -DestinationPortRange "443" | Set-AzNetworkSecurityGroup
```

Ardından, [PROXY1 yerel yönetici hesap](https://portal.azure.com) adı ve parolasını kullanarak PROXY1 sanal makinesine bağlanmak için Azure portalını kullanın ve sonra PROXY1'de Windows PowerShell istemini açın.
  
Ad çözümlemeyi ve PROXY1 ile DC1 arasındaki ağ iletişimini kontrol etmek için **, ping dc1.corp.contoso.com** komutu çalıştırın ve dört yanıt olduğunu kontrol edin.
  
Ardından, PROXY1'de komut isteminde bu komutları kullanarak PROXY1 sanal Windows PowerShell CORP etki alanına katılın.
  
```powershell
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

Yerel bilgisayarınızda bu proxy1 komutlarının Azure PowerShell IP adresini görüntüleme.
  
```powershell
Write-Host (Get-AzPublicIpaddress -Name "PROXY1-PIP" -ResourceGroup $rgName).IPAddress
```

Ardından, genel DNS sağlayıcınızla birlikte çalışabilirsiniz ve **fs.testlab** için yeni bir genel DNS A kaydı oluşturun.\<*your DNS domain name*> bu bağlantı, Ana Bilgisayar Yazma komutu tarafından görüntülenen IP **adresine çözüm** sağlar. **fs.testlab.**\<*your DNS domain name*> Bundan sonra federasyon hizmeti  *FQDN olarak adlandırılır*.
  
Ardından, CORPUser1\\ kimlik bilgilerini kullanarak DC1 sanal makinesine bağlanmak için [Azure portalını](https://portal.azure.com) kullanın ve sonra da yönetici düzeyinde bir komut isteminde Windows PowerShell çalıştırın:
  
```powershell
Add-DnsServerPrimaryZone -Name corp.contoso.com -ZoneFile corp.contoso.com.dns
Add-DnsServerResourceRecordA -Name "fs" -ZoneName corp.contoso.com -AllowUpdateAny -IPv4Address "10.0.0.100" -TimeToLive 01:00:00
```
Bu komutlar, Azure sanal ağının sanal ağ üzerinde sanal makinelerin iç federasyon hizmeti FQDN'sini ADFS1'in özel IP adresine çözecek şekilde bir iç DNS A kaydı oluşturmasını sağlar.
  
Sonuçta elde edilen yapılandırmanız şöyle görünüyor:
  
![Test ortamı için DirSync'e Microsoft 365.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase3.png)
  
## <a name="phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1"></a>Aşama 4: Otomatik olarak imzalanan sertifika oluşturma ve ADFS1 ve PROXY1'i yapılandırma

Bu aşamada, federasyon hizmeti FQDN'niz için otomatik olarak imzalanan bir dijital sertifika oluşturun ve ADFS1 ve PROXY1'i bir AD FS grubu olarak yapılandırın.
  
İlk olarak, CORPUser1 kimlik bilgilerini kullanarak DC1 sanal makinesine bağlanmak için [Azure portalını](https://portal.azure.com) kullanın ve sonra da yönetici\\ düzeyinde bir Windows PowerShell istemi açın.
  
Ardından, DC1'de Yer Alan Komut İstemi'nde bu Windows PowerShell bir AD FS hizmet hesabı oluşturun:
  
```powershell
New-ADUser -SamAccountName ADFS-Service -AccountPassword (read-host "Set user password" -assecurestring) -name "ADFS-Service" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```
Bu komutun hesap parolasını girmenizi istendiğinde unutmayın. Güçlü bir parola seçin ve güvenli bir konuma kaydedin. Bu aşama ve Aşama 5 için bu aşamaya ihtiyacınız olacak.
  
CORPUser1\\ kimlik bilgilerini kullanarak ADFS1 sanal makinesine bağlanmak için [Azure portalını](https://portal.azure.com) kullanın. ADFS1'Windows PowerShell yönetici düzeyinde bir komut istemi açın, federasyon hizmeti FQDN'nizi doldurun ve sonra otomatik olarak imzalanan sertifika oluşturmak için şu komutları çalıştırın:
  
```powershell
$fedServiceFQDN="<federation service FQDN>"
New-SelfSignedCertificate -DnsName $fedServiceFQDN -CertStoreLocation "cert:\LocalMachine\My"
New-Item -path c:\Certs -type directory
New-SmbShare -name Certs -path c:\Certs -changeaccess CORP\User1
```

Ardından, otomatik olarak imzalanan yeni sertifikayı dosya olarak kaydetmek için bu adımları kullanın.
  
1. **Başlat'ı** seçin, **mmc.exe** girin ve Enter tuşuna **basın**.
    
2. **FileAdd** > **/Remove Snap-in'i seçin**.
    
3. Ek **Bileşen Ekle veya Kaldır'da**, kullanılabilir ek bileşenler listesinde  Sertifikalar'a çift tıklayın, **Bilgisayar hesabı'yı** ve sonra da Sonraki'yi **seçin**.
    
4. Bilgisayar **Seç'de** **Son'a ve** sonra Tamam'a **tıklayın**.
    
5. Ağaç bölmesinde Sertifikalar'a **(Yerel Bilgisayar) veya Kişisel > Sertifikalar'> açın**.
    
6. Federasyon hizmeti FQDN'niz ile sertifikayı seçin ve tutun (veya sağ tıklayın), Tüm görevler'i seçin ve ardından Dışarı Aktar'ı **seçin**.
    
7. Hoş Geldiniz **sayfasında** Sonraki'yi **seçin**.
    
8. Özel Anahtarı **Dışarı Aktar sayfasında** Evet'i **seçin ve** sonra da Sonraki'yi **seçin**.
    
9. Dosya Biçimini **Dışarı Aktar sayfasında Tüm** genişletilmiş özellikleri **dışarı aktar'ı ve** sonra da Sonraki'yi **seçin**.
    
10. Güvenlik sayfasında **Parola'ya** tıklayın **ve Parola'ya** ve Parolayı **onayla'ya** bir **parola girin.**
    
11. Dışarı Aktar **dosya sayfasında Gözat'ı** **seçin**.
    
12. **C:Certs klasörüne\\** gidin, Dosya adı **alanına SSL** **girin ve Kaydet'i** **seçin.**
    
13. Dışarı Aktar **dosya sayfasında Sonraki'yi** **seçin**.
    
14. Sertifika Dışarı **Aktarma Sihirbazı tamamlanıyor sayfasında Son'a** **tıklayın**. Soruldiğinde Tamam'ı **seçin**.
    
Ardından, AD FS hizmetini ADFS1'de Windows PowerShell komut istemine şu komutu yükleyin:
  
```powershell
Install-WindowsFeature ADFS-Federation -IncludeManagementTools
```

Yüklemenin tamamlandıktan sonra tamamlandıktan sonraya kadar bekleyin.
  
Ardından, aşağıdaki adımlarla AD FS hizmetini yapılandırabilirsiniz:
  
1. **Başlat'ı** seçin ve sonra Sunucu **Yöneticisi simgesini** seçin.
    
2. Sunucu Yöneticisi'nin ağaç bölmesinde **AD FS'yi seçin**.
    
3. Üst çubukta yer alan araç çubuğunda, turuncu uyarı simgesini seçin ve sonra da Bu sunucuda **federasyon hizmetini yapılandır'ı seçin**.
    
4. Active Directory **Federasyon** Hizmetleri Yapılandırma Sihirbazı'nın Hoş Geldiniz sayfasında, Sonraki'yi **seçin**.
    
5. Ad **DS Bağlan seçin** sayfasında, Sonraki'yi **seçin**.
    
6. Hizmet **Özelliklerini Belirtin sayfasında** :
    
  - **SSL Sertifikası için** aşağı oku seçin ve sonra da federasyon hizmetinizin adı olan FQDN sertifikasını seçin.
    
  - Federasyon **Hizmeti Görünen Adı** alanına kurgusal kuruluş adının girin.
    
  - **İleri**'yi seçin.
    
7. Hizmet Hesabını **Belirtin sayfasında Hesap** adı için **Seç'i seçin**.
    
8. Kullanıcı **veya Hizmet Hesabı Seçin alanına** **ADFS-Hizmet girin, Adları** **Kontrol Et'i seçin ve** sonra da Tamam'ı **seçin**.
    
9. Hesap **Parolası alanına**, hesabın parolasını ADFS-Service ve Ardından Sonraki'yi **seçin**.
    
10. Yapılandırma Veritabanını **Belirtin sayfasında Sonraki'yi** **seçin**.
    
11. Gözden Geçirme **Seçenekleri sayfasında** Sonraki'yi **seçin**.
    
12. **Önkr– Denetimler sayfasında Yapılandır'ı** **seçin**.

13. Sonuçlar sayfasında **Kapat'ı** **seçin**.
    
14. **Başlat'ı** seçin, güç simgesini seçin, Yeniden **başlat'ı** seçin ve sonra da Devam'ı **seçin**.
    
[Azure portaldan](https://portal.azure.com) CORPUser1 hesap kimlik bilgileriyle PROXY1'e\\ bağlanın.
  
Ardından, otomatik olarak imzalanan sertifikayı hem **PROXY1'e hem de APP1'e yüklemek için bu adımları kullanın**.
  
1. **Başlat'ı** seçin, **mmc.exe** girin ve Enter tuşuna **basın**.
    
2. Ek **Bileşen >/Kaldır'ı seçin**.
    
3. Ek **Bileşen Ekle veya Kaldır'da**, kullanılabilir ek bileşenler listesinde  Sertifikalar'a çift tıklayın, **Bilgisayar hesabı'yı** ve sonra da Sonraki'yi **seçin**.
    
4. Bilgisayar **Seç'de** **Son'a ve** sonra Tamam'a **tıklayın**.
    
5. Ağaç bölmesinde Sertifikalar **(Yerel Bilgisayar)** > **PersonalCertificates'i** >  açın.
    
6. Kişisel'i seçin ve basılı tutun (veya sağ **tıklayın**), Tüm **görevler'i seçin ve** ardından İçeri Aktar'ı **seçin**.
    
7. Hoş Geldiniz **sayfasında** Sonraki'yi **seçin**.
    
8. İçeri **Aktarı Dosyası sayfasında** **adfs1certssl.pfx\\\\\\\\** girin ve ardından Sonraki'yi **seçin**.
    
9. Özel anahtar **koruması sayfasında** Parola alanına sertifika parolasını girin **ve Ardından** Sonraki'yi **seçin.**
    
10. Sertifika deposu **sayfasında Sonraki'yi** **seçin.**
    
11. Tamamla **sayfasında Son'a** **tıklayın**.
    
12. Sertifika Deposu **sayfasında Sonraki'yi** **seçin**.
    
13. Soruldiğinde Tamam'ı **seçin**.
    
14. Ağaç bölmesinde Sertifikalar'ı **seçin**.
    
15. Sertifikayı seçin ve basılı tutun (veya sağ tıklayın) ve ardından Kopyala'yı **seçin**.
    
16. Ağaç bölmesinde Güvenilen Kök Sertifika **YetkilileriCertificates'i** >  açın.
    
17. Fare işaretçinizi yüklü sertifikalar listesinin altına doğru hareket ettirin, seçin ve basılı tutun (veya sağ tıklayın) ve ardından Yapıştır'ı **seçin**.
    
Yönetici düzeyinde bir PowerShell komut istemini açın ve aşağıdaki komutu çalıştırın:
  
```powershell
Install-WindowsFeature Web-Application-Proxy -IncludeManagementTools
```

Yüklemenin tamamlandıktan sonra tamamlandıktan sonraya kadar bekleyin.
  
Web uygulaması ara sunucu hizmetini ADFS1'i federasyon sunucusu olarak kullanmak üzere yapılandırmak için bu adımları kullanın:
  
1. **Başlat'ı** ve sonra Sunucu **Yöneticisi'ni seçin**.
    
2. Ağaç bölmesinde Uzak **Erişim'i seçin**.
    
3. Üst çubukta yer alan araç çubuğunda turuncu uyarı simgesini seçin ve ardından Web Uygulaması Proxy **Sihirbazı'nı Aç'ı seçin**.
    
4. Web Uygulaması **Ara** Sunucu Yapılandırma Sihirbazı'nın Hoş Geldiniz sayfasında, Sonraki'yi **seçin**.
    
5. Federasyon **Sunucusu sayfasında** :
    
  - Federasyon **hizmeti adı kutusuna** , federasyon hizmeti FQDN'nizi girin.
    
  - Kullanıcı adı **kutusuna** **CORPUser1\\ girin**.
    
  - Parola **kutusuna** , Kullanıcı1 hesabının parolasını girin.
    
  - **İleri**'yi seçin.
    
6. **AD FS Proxy Sertifikası sayfasında** aşağı oku seçin, federasyon hizmetinizin FQDN'olduğu sertifikayı seçin ve sonra da Sonraki'yi **seçin**.
    
7. Onay sayfasında **Yapılandır'ı** **seçin**.
    
8. Sonuçlar sayfasında **Kapat'ı** **seçin**.
    
## <a name="phase-5-configure-microsoft-365-for-federated-identity"></a>Aşama 5: Federasyon Microsoft 365 yapılandırma

CORPUser1\\ hesap kimlik bilgileriyle APP1 sanal makinesine bağlanmak için [Azure portalını](https://portal.azure.com) kullanın.
  
Federasyon kimlik doğrulaması için Azure AD Bağlan ve Microsoft 365 aboneliğinizi yapılandırmak için bu adımları kullanın:
  
1. Masaüstünden **Azure AD Destek Hizmetleri'ne çift Bağlan**.
    
2. **Azure AD'ye Hoş Geldiniz Bağlan** Yapılandır'ı **seçin**.
    
3. Ek görevler **sayfasında,** Kullanıcı oturum açma **ayarlarını değiştir'i seçin ve** sonra da Sonraki'yi **seçin**.
    
4. **Azure AD'Bağlan** oturum açın sayfasında genel yönetici hesap adı ve parolanızı girin ve ardından Sonraki'yi **seçin**.
    
5. Kullanıcı oturum **açma sayfasında,** AD **FS ile Federasyon'ı seçin ve sonra** da Sonraki'yi **seçin**.
    
6. **AD FS sunucu grubu sayfasında** Varolan **bir AD FS** sunucu grubu kullan'ı seçin, Sunucu Adı kutusuna **ADFS1** girin ve sonra da Sonraki'yi **seçin**.
    
7. Sunucu kimlik bilgileri istendiğinde CORPUser1\\ hesabının kimlik bilgilerini girin ve Tamam'ı **seçin**.
    
8. Etki Alanı **Yöneticisi kimlik** bilgileri sayfasında, Kullanıcı adı kutusuna **CORPUser1\\** girin, Parola kutusuna hesap parolasını girin **ve sonra Da** Sonraki'yi **seçin**.
    
9. **AD FS hizmet** hesabı sayfasında, Etki Alanı Kullanıcı Adı kutusuna **CORPADFS-Service\\** girin, Etki Alanı Kullanıcı Parolası kutusuna hesap parolasını girin  ve ardından Sonraki'yi **seçin**.
    
10. **Azure AD Etki Alanı sayfasındaki** **Etki** Alanı'nın altında, Daha önce oluşturduğunuz ve Aşama 1'de aboneliğinize ekley istediğiniz etki alanının adını seçin ve sonra da Sonraki'yi **seçin**.
    
11. Yapılandırmaya **hazır sayfasında Yapılandır'ı** **seçin**.
    
12. Yükleme tamamlandı **sayfasında Doğrula'ya** **tıklayın**.
    
    Hem intranet hem de İnternet yapılandırmasının doğrulanmış olduğunu belirten iletiler görüyor olun.
    
13. Yükleme tamamlandı **sayfasında Çıkış'ı** **seçin**.
    
Federasyon kimlik doğrulamasının çalıştığını göstermek için:
  
1. Yerel bilgisayarınızda tarayıcınızın yeni özel örneğini açın ve 'a gidin [https://admin.microsoft.com](https://admin.microsoft.com).
    
2. Oturum açma kimlik bilgileri için oturum açma bilgilerini **user1@**\<*the domain created in Phase 1*>.
    
    Örneğin, test etki alanınız **testlab.contoso.com,** "Etki alanı" user1@testlab.contoso.com. Sekme **tuşuna basın** veya diğer Microsoft 365 otomatik olarak yeniden yönlendirmesine izin verme.
    
    Artık Bağlantınız özel **bir sayfa** değil. Bunu, masaüstü bilgisayarınızda doğrulanamadı adFS1 üzerine otomatik olarak imzalanan bir sertifika yüklemiş olduğunuz için görüyoruz. Federasyon kimlik doğrulamasının üretim dağıtımında, güvenilir bir sertifika yetkilisinin sertifikasını kullanırsanız, kullanıcılarınız bu sayfayı göremz.
    
3. Bağlantınız **özel değil sayfasında Gelişmiş'i** seçin **ve** sonra **İleri'yi seçin \<*your federation service FQDN*>**. 
    
4. Kurgusal kuruluş adının olduğu sayfada, aşağıdakilerle oturum açma:
    
  - **CORP\\ Ad için kullanıcı1**
    
  - Kullanıcı1 hesabının parolası
    
    Sayfa Giriş **Microsoft Office görüyoruz**.
    
Bu yordam, deneme aboneliğinizin DC1'de barındırılan AD DS corp.contoso.com etki alanıyla federasyon olduğunu belirtir. Kimlik doğrulama işleminin temelleri şöyledir:
  
1. Aşama 1'de oturum açma hesabı adıyla oluşturduğunuz federasyon etki alanını kullanırsanız, Microsoft 365 tarayıcınızı federasyon hizmeti FQDN ve PROXY1'inize yeniden yönlendirmektedir.
    
2. PROXY1, yerel bilgisayarınıza kurgusal şirketin oturum açma sayfasını gönderir.
    
3. CORPUser1'i\\ ve parolayı PROXY1'e gönderirken, bunları ADFS1'e iletir.
    
4. ADFS1 CORPUser1\\ ve parolayı DC1 ile doğrular ve yerel bilgisayarınıza bir güvenlik belirteci gönderir.
    
5. Yerel bilgisayarınız güvenlik belirteci posta Microsoft 365.
    
6. Microsoft 365 belirteci ADFS1 tarafından oluşturulmuş olduğunu doğrular ve erişime izin verir.
    
Deneme aboneliğiniz artık federasyon kimlik doğrulamasıyla yapılandırılmış. Gelişmiş kimlik doğrulama senaryoları için bu geliştirme/sınama ortamını kullanabilirsiniz.
  
## <a name="next-step"></a>Sonraki adım

Azure'da iş için üretime hazır Microsoft 365, yüksek kullanılabilirli federasyon kimlik doğrulamasını dağıtmaya hazırsanız, bkz. Azure'da Microsoft 365 federasyon kimlik [doğrulamasını dağıtma](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md).
  
