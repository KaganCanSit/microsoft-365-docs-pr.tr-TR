---
title: Puppet ile Linux'ta Uç Nokta için Microsoft Defender dağıtma
ms.reviewer: ''
description: Puppet kullanarak Linux'ta Uç Nokta için Microsoft Defender dağıtmayı açıklar.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, linux, installation, deploy, uninstallation, puppet, ansible, linux, redhat, ubuntu, debian, sles, suse, centos, fedora, amazon linux 2
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 9fe38f8bec7ca99d9c1828126382c8f70a22fa3a
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014614"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-linux-with-puppet"></a>Puppet ile Linux'ta Uç Nokta için Microsoft Defender dağıtma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Bu makalede Puppet kullanarak Linux'ta Uç Nokta için Defender'ın nasıl dağıtılacağı açıklanır. Başarılı bir dağıtım için aşağıdaki görevlerin tümünün tamamlanması gerekir:

- [Ekleme paketini indirme](#download-the-onboarding-package)
- [Puppet bildirimi oluşturma](#create-a-puppet-manifest)
- [Dağıtım](#deployment)
- [Ekleme durumunu denetleme](#check-onboarding-status)

## <a name="prerequisites-and-system-requirements"></a>Önkoşullar ve sistem gereksinimleri

 Geçerli yazılım sürümü için önkoşulların ve sistem gereksinimlerinin açıklaması [için Linux'ta Uç Nokta için Ana Defender sayfasına](microsoft-defender-endpoint-linux.md) bakın.

Ayrıca Puppet dağıtımı için Puppet yönetim görevleri hakkında bilgi sahibi olmanız, Puppet'ın yapılandırılmasını sağlamanız ve paketlerin nasıl dağıtıldığını bilmeniz gerekir. Puppet'ın aynı görevi tamamlamak için birçok yolu vardır. Bu yönergelerde, paketin dağıtılmasına yardımcı olmak için *apt* gibi desteklenen Puppet modüllerinin kullanılabilir olduğu varsayılır. Kuruluşunuz farklı bir iş akışı kullanabilir. Ayrıntılar için [Puppet belgelerine](https://puppet.com/docs) bakın.

## <a name="download-the-onboarding-package"></a>Ekleme paketini indirme

Ekleme paketini Microsoft 365 Defender portalından indirin:

1. Microsoft 365 Defender portalında **Ayarlar > Uç Noktalar > Cihaz yönetimi > Ekleme'ye** gidin.
2. İlk açılan menüde işletim sistemi olarak **Linux Server'ı** seçin. İkinci açılan menüde dağıtım yöntemi olarak **Tercih ettiğiniz Linux yapılandırma yönetim aracını** seçin.
3. **Ekleme paketini indir'i** seçin. Dosyayı WindowsDefenderATPOnboardingPackage.zip olarak kaydedin.

   :::image type="content" source="images/portal-onboarding-linux-2.png" alt-text="Eklenen paketi indirme seçeneği" lightbox="images/portal-onboarding-linux-2.png":::

4. Komut isteminden, dosyanın size ait olduğunu doğrulayın. 

    ```bash
    ls -l
    ```

    ```Output
    total 8
    -rw-r--r-- 1 test  staff  4984 Feb 18 11:22 WindowsDefenderATPOnboardingPackage.zip
    ```

5. Arşivin içeriğini ayıklayın.

    ```bash
    unzip WindowsDefenderATPOnboardingPackage.zip
    ```

    ```Output
    Archive:  WindowsDefenderATPOnboardingPackage.zip
    inflating: mdatp_onboard.json
    ```

## <a name="create-a-puppet-manifest"></a>Puppet bildirimi oluşturma

Linux'ta Uç Nokta için Defender'ı Puppet sunucusu tarafından yönetilen cihazlara dağıtmak için bir Puppet bildirimi oluşturmanız gerekir. Bu örnek, puppetlab'lerden kullanılabilen *apt* ve *yumrepo* modüllerini kullanır ve modüllerin Puppet sunucunuza yüklendiğini varsayar.

Puppet yüklemenizin modules klasörünün altında klasörleri *install_mdatp/dosyalar* ve *install_mdatp/bildirimler* oluşturun. Bu klasör genellikle Puppet sunucunuzdaki */etc/puppetlabs/code/environments/production/modules* konumunda bulunur. Yukarıda oluşturulan mdatp_onboard.json dosyasını *install_mdatp/files* klasörüne kopyalayın. *init.pp* oluşturma dağıtım yönergelerini içeren dosya:

```bash
pwd
```

```Output
/etc/puppetlabs/code/environments/production/modules
```

```bash
tree install_mdatp
```

```Output
install_mdatp
├── files
│   └── mdatp_onboard.json
└── manifests
    └── init.pp
```

### <a name="contents-of-install_mdatpmanifestsinitpp"></a>İçeriği `install_mdatp/manifests/init.pp`

Linux'ta Uç Nokta için Defender aşağıdaki kanallardan birinden dağıtılabilir (aşağıda *[channel]* olarak belirtilir): *insider-fast*, *insider-slow* veya *prod*. Bu kanalların her biri bir Linux yazılım deposuna karşılık gelir.

Kanal seçimi, cihazınıza sunulan güncelleştirmelerin türünü ve sıklığını belirler. *Insider'ların hızlı* olduğu cihazlar, güncelleştirmeleri ve yeni özellikleri ilk alan cihazlardır ve daha sonra *insider'ların yavaş* ve son olarak *prod* tarafından takip edilir.

Yeni özellikleri önizlemek ve erken geri bildirim sağlamak için kuruluşunuzdaki bazı cihazları *insider hızlı veya insider yavaş* kullanacak şekilde yapılandırmanız önerilir.

> [!WARNING]
> İlk yüklemeden sonra kanalın değiştirilmesi için ürünün yeniden yüklenmesi gerekir. Ürün kanalını değiştirmek için: Mevcut paketi kaldırın, cihazınızı yeni kanalı kullanacak şekilde yeniden yapılandırın ve paketi yeni konumdan yüklemek için bu belgedeki adımları izleyin.

Dağıtımınızı ve sürümünüzü not edin ve altında `https://packages.microsoft.com/config/[distro]/`onun için en yakın girdiyi belirleyin.

Aşağıdaki komutlarda *[distro]* ve *[version]* sözcüklerini tanımladığınız bilgilerle değiştirin:

> [!NOTE]
> RedHat, Oracle Linux, Amazon Linux 2 ve CentOS 8 olması durumunda *[distro]* yerine 'rhel' yazın.

```puppet
# Puppet manifest to install Microsoft Defender for Endpoint on Linux.
# @param channel The release channel based on your environment, insider-fast or prod.
# @param distro The Linux distribution in lowercase. In case of RedHat, Oracle Linux, Amazon Linux 2, and CentOS 8, the distro variable should be 'rhel'.
# @param version The Linux distribution release number, e.g. 7.4.

class install_mdatp (
$channel = 'insiders-fast',
$distro = undef,
$version = undef
){
    case $::osfamily {
        'Debian' : {
        $release = $channel ? {
        'prod' => $facts['os']['distro']['codename']
        default => $channel
        }
            apt::source { 'microsoftpackages' :
                location => "https://packages.microsoft.com/${distro}/${version}/prod",
                release  =>  $release,
                repos    => 'main',
                key      => {
                    'id'     => 'BC528686B50D79E339D3721CEB3E94ADBE1229CF',
                    'server' => 'keyserver.ubuntu.com',
                },
            }
        }
        'RedHat' : {
            yumrepo { 'microsoftpackages' :
                baseurl  => "https://packages.microsoft.com/${distro}/${version}/${channel}",
                descr    => "packages-microsoft-com-prod-${channel}",
                enabled  => 1,
                gpgcheck => 1,
                gpgkey   => 'https://packages.microsoft.com/keys/microsoft.asc'
            }
        }
        default : { fail("${::osfamily} is currently not supported.") }
    }

    case $::osfamily {
        /(Debian|RedHat)/: {
            file { ['/etc/opt', '/etc/opt/microsoft', '/etc/opt/microsoft/mdatp']:
                ensure => directory,
                owner  => root,
                group  => root,
                mode   => '0755'
            }

            file { '/etc/opt/microsoft/mdatp/mdatp_onboard.json':
                source  => 'puppet:///modules/install_mdatp/mdatp_onboard.json',
                owner   => root,
                group   => root,
                mode    => '0600',
                require => File['/etc/opt/microsoft/mdatp']
            }

            package { 'mdatp':
                ensure  => 'installed',
                require => File['/etc/opt/microsoft/mdatp/mdatp_onboard.json']
            }
        }
        default : { fail("${::osfamily} is currently not supported.") }
    }
}
```

## <a name="deployment"></a>Dağıtım

Yukarıdaki bildirimi sitenize ekleyin.pp Dosya:

```bash
cat /etc/puppetlabs/code/environments/production/manifests/site.pp
```

```Output
node "default" {
    include install_mdatp
}
```

Kayıtlı aracı cihazları Puppet Server'ı düzenli aralıklarla yoklar ve algılanır algılanmaz yeni yapılandırma profillerini ve ilkelerini yükler.

## <a name="monitor-puppet-deployment"></a>Puppet dağıtımlarını izleme

Aracı cihazında şunları çalıştırarak ekleme durumunu da de kontrol edebilirsiniz:

```bash
mdatp health
```

```Output
...
licensed                                : true
org_id                                  : "[your organization identifier]"
...
```

- **lisanslı**: Bu, cihazın kuruluşunuza bağlı olduğunu onaylar.

- **orgId**: Bu, Uç Nokta için Defender kuruluş tanımlayıcınızdır.

## <a name="check-onboarding-status"></a>Ekleme durumunu denetleme

Bir betik oluşturarak cihazların doğru şekilde eklenip eklenmediğini de kontrol edebilirsiniz. Örneğin, aşağıdaki betik kayıtlı cihazları ekleme durumu açısından denetler:

```bash
mdatp health --field healthy
```

Yukarıdaki komut, ürünün eklenip eklenmediğini ve beklendiği gibi çalıştığını yazdırır `1` .

> [!IMPORTANT]
> Ürün ilk kez başlatıldığında en son kötü amaçlı yazılımdan koruma tanımlarını indirir. İnternet bağlantınıza bağlı olarak bu işlem birkaç dakika kadar sürebilir. Bu süre boyunca yukarıdaki komut değerini `0`döndürür.

Ürün iyi durumda değilse çıkış kodu (üzerinden `echo $?`denetlenebilir) sorunu gösterir:

- Cihaz henüz eklenmemişse 1.
- Daemon bağlantısı kurulamıyorsa 3.

## <a name="log-installation-issues"></a>Günlük yükleme sorunları

 Bir hata oluştuğunda yükleyici tarafından oluşturulan otomatik olarak oluşturulan günlüğü bulma hakkında daha fazla bilgi için bkz [. Günlük yükleme sorunları](linux-resources.md#log-installation-issues).

## <a name="operating-system-upgrades"></a>İşletim sistemi yükseltmeleri

İşletim sisteminizi yeni bir ana sürüme yükseltirken, önce Linux'ta Uç Nokta için Defender'ı kaldırmanız, yükseltmeyi yüklemeniz ve son olarak cihazınızda Linux'ta Uç Nokta için Defender'ı yeniden yapılandırmanız gerekir.

## <a name="uninstallation"></a>Kaldırma

*init.pp* *dosyasında* aşağıdaki içeriklere sahip *install_mdatp* benzer bir modül remove_mdatp oluşturun Dosya:

```bash
class remove_mdatp {
    package { 'mdatp':
        ensure => 'purged',
    }
}
```
