---
title: Chef ile Linux'ta Uç Nokta için Defender'ı Dağıtma
description: Chef ile Linux'ta Uç Nokta için Defender'ı dağıtmayı öğrenin
keywords: microsoft, defender, atp, linux, scans, virüsten koruma, uç nokta için microsoft defender (linux)
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: lovina-saldanha
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 8f610821b6c0bef7694d6ce8acd256f59f761f06
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65872950"
---
# <a name="deploy-defender-for-endpoint-on-linux-with-chef"></a>Uç Nokta için Defender’ı Chef ile Linux üzerinde dağıtın

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Başlamadan önce: Henüz yüklü değilse sıkıştırmayı açın.

Chef bileşenleri zaten yüklüdür ve Chef tarafından yönetilen Linux sunucularında Uç Nokta için Defender'a dağıtmak için kullanılacak yemek kitabını depolamak için bir Chef deposu (chef oluşturma deposu \<reponame\>) vardır.

Chef deponuzdaki cookbooks klasörünün içinden aşağıdaki komutu çalıştırarak mevcut deponuzda yeni bir yemek kitabı oluşturabilirsiniz:

```bash
chef generate cookbook mdatp
```

Bu komut, yeni yemek kitabı için mdatp adlı yeni bir klasör yapısı oluşturur. MDE dağıtımını eklemek için kullanmak istediğiniz bir yemek kitabınız varsa mevcut bir yemek kitabını da kullanabilirsiniz.
Yemek kitabı oluşturulduktan sonra, yeni oluşturulan yemek kitabı klasörünün içinde bir dosyalar klasörü oluşturun:

```bash
mkdir mdatp/files
```

Microsoft 365 Defender portalından indirilebilen Linux Server Ekleme zip dosyasını bu yeni dosyalar klasörüne aktarın.

Chef workstation'da mdatp/recipes klasörüne gidin. Bu klasör, yemek kitabı oluşturulduğunda oluşturulur. Default.rb dosyasının sonuna aşağıdaki yönergeleri eklemek için tercih ettiğiniz metin düzenleyiciyi (vi veya nano gibi) kullanın:

- '::onboard_mdatp' include_recipe
- '::install_mdatp' include_recipe

Ardından default.rb dosyasını kaydedin ve kapatın.

Ardından, recipes klasöründe install_mdatp.rb adlı yeni bir tarif dosyası oluşturun ve bu metni dosyaya ekleyin:

```powershell
#Add Microsoft Defender
Repo
case node['platform_family']
when 'debian'
 apt_repository 'MDAPRepo' do
   arch               'amd64'
   cache_rebuild      true
   cookbook           false
   deb_src            false
   key                'BC528686B50D79E339D3721CEB3E94ADBE1229CF'
   keyserver          "keyserver.ubuntu.com"
   distribution       'focal'
   repo_name          'microsoft-prod'
   components         ['main']
   trusted            true
   uri                "https://packages.microsoft.com/config/ubuntu/20.04/prod"
 end
 apt_package "mdatp"
when 'rhel'
 yum_repository 'microsoft-prod' do
   baseurl            "https://packages.microsoft.com/config/rhel/7/prod/"
   description        "Microsoft Defender for Endpoint"
   enabled            true
   gpgcheck           true
   gpgkey             "https://packages.microsoft.com/keys/microsoft.asc"
 end
 if node['platform_version'] <= 8 then
    yum_package "mdatp"
 else
    dnf_package "mdatp"
 end
end
```

Sürüm numarasını, dağıtımını ve depo adını dağıtacağınız sürümle ve dağıtmak istediğiniz kanalla eşleşecek şekilde değiştirmeniz gerekir.
Ardından, mdatp/recipies klasöründe bir onboard_mdatp.rb dosyası oluşturmanız gerekir. Bu dosyaya aşağıdaki metni ekleyin:

```powershell
#Create MDATP Directory
mdatp = "/etc/opt/microsoft/mdatp"
zip_path = "/path/to/chef-repo/cookbooks/mdatp/files/WindowsDefenderATPOnboardingPackage.zip"

directory "#{mdatp}" do
  owner 'root'
  group 'root'
  mode 0755
  recursive true
end

#Extract WindowsDefenderATPOnbaordingPackage.zip into /etc/opt/microsoft/mdatp

bash 'Extract Onbaording Json MDATP' do
  code <<-EOS
  unzip #{zip_path} -d #{mdatp}
  EOS
  not_if { ::File.exist?('/etc/opt/microsoft/mdatp/mdatp_onboard.json') }
end
```

Yol adını ekleme dosyasının konumuna güncelleştirdiğinden emin olun.
Chef iş istasyonunda dağıtmayı test etmek için komutunu çalıştırmanız ``sudo chef-client -z -o mdatp``gerekir.
Dağıtımınızdan sonra[, Linux'ta Uç Nokta için Microsoft Defender için tercihleri ayarlama temelinde sunuculara](/microsoft-365/security/defender-endpoint/linux-preferences) bir yapılandırma dosyası oluşturmayı ve dağıtmayı göz önünde bulundurmanız gerekir.
Yapılandırma dosyanızı oluşturup test ettikten sonra, ekleme paketini de yerleştirdiğiniz cookbook/mdatp/files klasörüne yerleştirebilirsiniz. Ardından mdatp/recipies klasöründe bir settings_mdatp.rb dosyası oluşturabilir ve şu metni ekleyebilirsiniz:

```powershell
#Copy the configuration file
cookbook_file '/etc/opt/microsoft/mdatp/managed/mdatp_managed.json' do
  source 'mdatp_managed.json'
  owner 'root'
  group 'root'
  mode '0755'
  action :create
end
```

Bu adımı tarifin bir parçası olarak eklemek için, tarif klasöründeki default.rb dosyanıza ':: settings_mdatp' include_recipe eklemeniz gerekir.
Otomatik güncelleştirmeleri zamanlamak için crontab'ı da kullanabilirsiniz [Uç Nokta için Microsoft Defender (Linux) güncelleştirmesini zamanlayın](linux-update-MDE-Linux.md).

MDATP yemek kitabını kaldırın:

```powershell
#Uninstall the Defender package
case node['platform_family']
when 'debian'
 apt_package "mdatp" do
   action :remove
 end
when 'rhel'
 if node['platform_version'] <= 8
then
    yum_package "mdatp" do
      action :remove
    end
 else
    dnf_package "mdatp" do
      action :remove
    end
 end
end
```
