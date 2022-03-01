---
title: Linux ile Linux'ta Uç Nokta için Defender'ı Dağıtma
description: Linux with Linux'ta Endpoint için Defender'ı dağıtmayı öğrenin
keywords: microsoft, defender, atp, linux, taramalar, virüsten koruma, uç nokta için microsoft defender (linux)
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
ms.openlocfilehash: 799fc4d163b120b4197b6cd044efe4740e4a3cc7
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63034246"
---
# <a name="deploy-defender-for-endpoint-on-linux-with-chef"></a>Linux'ta Linux'ta Linux'ta Endpoint için Deploy Defender

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Başlamadan önce: Henüz yüklenmemişse sıkıştırmayı açın.

Components bileşenleri zaten yüklenir ve Linux'un yönetilen Linux sunucularında Uç Nokta için Defender'a dağıtmak üzere kullanılacak yemek kitabını depolamak için bir Mağaza havuzu (kendi \<reponame\>deposunu) içerir.

Var olan depoda, deponun içinde bulunan yemek kitapları klasörünün içinde aşağıdaki komutu çalıştırarak yeni bir yemek kitabı oluşturabilirsiniz:

```bash
chef generate cookbook mdatp
```

Bu komut, mdatp adlı yeni yemek kitabı için yeni bir klasör yapısı oluşturur. MDE dağıtımını eklemek için kullanmak istediğiniz bir yemek kitabı varsa, var olan bir yemek kitabını da kullanabilirsiniz.
Yemek kitabı oluşturulduktan sonra, yemek kitabı klasörünün içinde yeni oluşturulan bir dosyalar klasörü oluşturun:

```bash
mkdir mdatp/files
```

Microsoft 365 Defender portalında indirilebilen Linux Server Onboarding zip dosyasını bu yeni dosyalar klasörüne aktarın.

İş Istasyonu'na gidip mdatp/recipes klasörüne gidin. Yemek kitabı oluşturulduğunda bu klasör oluşturulur. Default.rb dosyasının sonuna aşağıdaki yönergeleri eklemek için tercih ettiğiniz metin düzenleyicisini (vi veya nano gibi) kullanın:

- include_recipe::onboard_mdatp'
- include_recipe::install_mdatp'

Ardından default.rb dosyasını kaydedin ve kapatın.

Ardından yemek tarifleri klasöründeki install_mdatp.rb adlı yeni bir yemek tarifi dosyası oluşturun ve dosyaya bu metni ekleyin:

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

Sürüm numarasını, dağıtımını yapmak istediğiniz sürümle ve dağıtmak istediğiniz kanalla eşlanacak şekilde dağıtmanız ve yeniden dağıtmanız gerekir.
Ardından, mdatp/recipies klasöründe onboard_mdatp.rb dosyası oluşturmanız gerekir. Bu dosyaya aşağıdaki metni ekleyin:

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

Yol adını ekleme dosyasının bulunduğu konuma güncelleştirin.
Bunu İş istasyonu üzerinde dağıtın diye test etmek için yalnızca şunu çalıştırın ``sudo chef-client -z -o mdatp``: .
Dağıtımınız sonrasında Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarla'ya göre yapılandırma dosyası oluşturmayı ve [sunuculara dağıtmayı düşünebilirsiniz](/linux-preferences.md).
Yapılandırma dosyanızı oluşturduktan ve test ettikten sonra, bunu yemek kitabı/mdatp/files klasörüne yerleştirebilirsiniz; burada ekleme paketini de yerleştirebilirsiniz. Ardından mdatp/recipies klasöründe bir settings_mdatp.rb dosyası oluşturabilir ve şu metni ebilirsiniz:

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

Bu adımı yemek tarifinin bir parçası olarak eklemek için yemek tarifi klasöründeki default.rb include_recipe': settings_mdatp'i ekleyin.
Ayrıca, crontab'ı kullanarak otomatik güncelleştirmeleri zamanlamayı da kullanabilirsiniz. Uç Nokta [(Linux) için Microsoft Defender'a bir güncelleştirme zamanlama](linux-update-MDE-Linux.md).

MDATP yemek kitabını kaldırma:

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
