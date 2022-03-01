---
title: Linux'ta Linux'ta Uç Nokta için Microsoft Defender'ı Dağıtın
ms.reviewer: ''
description: "Linux'ta Uç Nokta için Microsoft Defender'ın Linux'ta Nasıl Dağıtıılları Açıklamaktadır: Linux'u Kullanarak Uç Nokta için Microsoft Defender'ın Nasıl Dağıtın?"
keywords: microsoft, defender, Endpoint için Microsoft Defender, linux, yükleme, dağıtma, kaldırma, atlanabilir, linux, redhat, ubuntu, debian, sles, suse, centos, fedora, amazon linux 2
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
ms.openlocfilehash: 305dd74d31f3cbbf07db23f8de89b2b57fe52326
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2022
ms.locfileid: "63016322"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-linux-with-puppet"></a>Linux'ta Linux'ta Uç Nokta için Microsoft Defender'ı Dağıtın

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Bu makalede, Linux'ta Linux'ta Uç Nokta için Defender'ın nasıl dağıt olduğu açıklanmıştır. Başarılı bir dağıtım için aşağıdaki görevlerin tamamlanmasını gerekir:

- [Ekleme paketini indirin](#download-the-onboarding-package)
- [Oluşturmak Kullanıcı bildirimi](#create-a-puppet-manifest)
- [Dağıtım](#deployment)
- [Ekleme durumunu denetleme](#check-onboarding-status)

## <a name="prerequisites-and-system-requirements"></a>Önkoşullar ve sistem gereksinimleri

 Geçerli yazılım sürümünün önkoşullarının ve sistem gereksinimlerinin açıklaması için [Linux'ta uç nokta için ana Defender sayfasına bakın](microsoft-defender-endpoint-linux.md).

Buna ek olarak,Ssık dağıtımı için, Sunucu yönetimi görevlerini biliyor, 1992'yi yapılandırmanız ve paketlerin nasıl dağıtıldığından emin olmak gerekir. Hasan'ın aynı görevi tamamlamak için birçok yolu vardır. Bu yönergelerde, paketin dağıtımına yardımcı olmak için birpt gibi desteklenen *Modüller* kullanılabilirliği varsayıldı. Organizasyonunız farklı bir iş akışı kullanabilir. Ayrıntılar için [Belge belgelerine](https://puppet.com/docs) bakın.

## <a name="download-the-onboarding-package"></a>Ekleme paketini indirin

Kullanıcı portalı üzerinden ekleme Microsoft 365 Defender indirin:

1. Uygulama Microsoft 365 Defender, Uç Noktaları **Ayarlar > Ve Cihaz yönetimi >'e > gidin**.
2. İlk açılan menüde işletim sistemi olarak **Linux Server'ı** seçin. İkinci açılan menüde dağıtım yöntemi olarak **Tercih ettiğiniz Linux yapılandırma yönetim aracı'nı** seçin.
3. Ekleme **paketini indir'i seçin**. Dosyayı farklı bir WindowsDefenderATPOnboardingPackage.zip.

    ![Microsoft 365 Defender portalın ekran görüntüsü.](images/portal-onboarding-linux-2.png)

4. Komut isteminden, dosyanın size ait olduğunu doğrulayın. 

    ```bash
    ls -l
    ```
    ```Output
    total 8
    -rw-r--r-- 1 test  staff  4984 Feb 18 11:22 WindowsDefenderATPOnboardingPackage.zip
    ```
5. Arşivin içeriğini ayıklar.
    ```bash
    unzip WindowsDefenderATPOnboardingPackage.zip
    ```
    ```Output
    Archive:  WindowsDefenderATPOnboardingPackage.zip
    inflating: mdatp_onboard.json
    ```

## <a name="create-a-puppet-manifest"></a>Bildirim oluşturma

Linux'ta Uç Nokta için Defender'ı Bir Sunucu tarafından yönetilen cihazlara dağıtmak için Bir Bildirim bildirimi oluşturmanız gerekir. Bu örnekte, *apt* ve *yerrepo* modüllerininlabs tarafından kullanılabilir ve modüller Tahmin sunucunuza yüklenmiş olduğu varsayıldı.

Özel/install_mdatp */dosyalar ve* *install_mdatp/bildirimlerinizin* modüller klasöründe oluşturun. Bu klasör tipik olarak, Sunucu *sunucunuzda /etc/labs/code/environments/production/modules* içinde bulunur. Yukarıda oluşturulan mdatp_onboard.json dosyasını install_mdatp */files klasörüne* kopyalayın. *Init.pp oluşturma* dağıtım yönergelerini içeren dosya:

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

### <a name="contents-of-install_mdatpmanifestsinitpp"></a>İçindekiler `install_mdatp/manifests/init.pp`

Linux'ta Uç Nokta için Defender aşağıdaki kanallardan biri (*[kanal]* olarak açıklanmıştır) *dağıtılabilir*: *insider hızlı*, *insider-slow* veya prod. Bu kanalların her biri bir Linux yazılım deposuna karşılık geldi.

Kanalın seçimi, cihazınıza sunulan güncelleştirmelerin türünü ve sıklığını belirler. Insider *hızlı olan cihazlar,* güncelleştirmeleri ve yeni özellikleri alan ilk cihazlardır ve bunu daha sonra *Insider yavaş* ve son olarak *prod takip edin*.

Yeni özelliklerin önizlemesini görüntülemek ve erken geri bildirim sağlamak için, kuruluş içindeki bazı cihazları *Insider hızlı veya insider-slow* kullanmaya yönelik olarak *yapılandırmanız önerilir*.

> [!WARNING]
> İlk yüklemeden sonra kanalı değiştirmek için ürünün yeniden yüklenmesi gerekir. Ürün kanalını değiştirmek için: var olan paketi kaldırın, cihazınızı yeni kanalı kullanmak üzere yeniden yapılandırın ve paketi yeni konumdan yüklemek için bu belge'de yer alan adımları izleyin.

Dağıtımınızı ve sürümünizi not edin ve altında ona en yakın girişi tanımlayabilirsiniz `https://packages.microsoft.com/config/[distro]/`.

Aşağıdaki komutlarda, *[distro]* ve *[version]* ifadelerini tanımdığer bilgilerle değiştirin:

> [!NOTE]
> RedHat, Oracle Linux, Amazon Linux 2 ve CentOS 8'de ise *[dağıtım]* yerine 'rhel' değiştirin.

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
            apt::source { 'microsoftpackages' :
                location => "https://packages.microsoft.com/config/${distro}/${version}/prod",
                release  => $channel,
                repos    => 'main',
                key      => {
                    'id'     => 'BC528686B50D79E339D3721CEB3E94ADBE1229CF',
                    'server' => 'keyserver.ubuntu.com',
                },
            }
        }
        'RedHat' : {
            yumrepo { 'microsoftpackages' :
                baseurl  => "https://packages.microsoft.com/config/${distro}/${version}/${channel}",
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

Yukarıdaki bildirimi sitenize.pp'ye dahil edin dosya:

```bash
cat /etc/puppetlabs/code/environments/production/manifests/site.pp
```
```Output
node "default" {
    include install_mdatp
}
```

Kayıtlı aracı cihazları Düzenli aralıklarla Sunucu'da yoklar ve algılandığında yeni yapılandırma profillerini ve ilkelerini yükleyin.

## <a name="monitor-puppet-deployment"></a>Monitör Dağıtımı

Aracı cihazında, şu çalıştırmayı çalıştırarak ekleme durumunu da kontrol edebilirsiniz:

```bash
mdatp health
```
```Output
...
licensed                                : true
org_id                                  : "[your organization identifier]"
...
```

- **lisanslı**: Bu, cihazın cihazınıza bağlı olduğunu onaylar.

- **orgId**: Bu, Uç nokta kuruluş tanımlayıcısı için Defender'nızdır.

## <a name="check-onboarding-status"></a>Ekleme durumunu denetleme

Bir betik oluşturarak, cihazların doğru şekilde yerleşik olup olmadığını kontrol edin. Örneğin, aşağıdaki betik, kayıtlı cihazların ekleme durumunu denetler:

```bash
mdatp health --field healthy
```

Ürün, işe alındı `1` ve beklendiği gibi çalışıyorsa, yukarıdaki komut yazdırılır.

> [!IMPORTANT]
> Ürün ilk kez başlatıldığında, en son kötü amaçlı yazılımdan koruma tanımlarını indirir. İnternet bağlantınıza bağlı olarak, bu birkaç dakika kadar sürebilir. Bu sırada yukarıdaki komut bir değeri döndürür `0`.

Ürün iyi değildir, çıkış kodu (üzerinden denetlen olabilir `echo $?`) sorunu gösterir:

- Cihaz henüz eklememişse 1.
- 3. daemon bağlantısı kurulamazsa.

## <a name="log-installation-issues"></a>Günlük yükleme sorunları

 Hata oluştuğunda yükleyici tarafından oluşturulan otomatik olarak oluşturulan günlüğü bulma hakkında daha fazla bilgi için bkz. [Günlük yükleme sorunları](linux-resources.md#log-installation-issues).

## <a name="operating-system-upgrades"></a>İşletim sistemi yükseltmeleri

İşletim sisteminizi yeni bir ana sürüme yükseltirken, önce Linux'ta Uç Nokta için Defender'ı kaldırmanız, yükseltmeyi yüklemeniz ve son olarak da cihazınıza Linux'ta Uç Nokta için Defender'ı yeniden yapılandırmanız gerekir.

## <a name="uninstallation"></a>Kaldırma

*init.pp* *remove_mdatp* içeriği *install_mdatp* benzer şekilde modül oluşturma dosya:

```bash
class remove_mdatp {
    package { 'mdatp':
        ensure => 'purged',
    }
}
```
