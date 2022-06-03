---
title: Linux'ta Uç Nokta için Microsoft Defender el ile dağıtma
ms.reviewer: ''
description: Komut satırından Linux'ta Uç Nokta için Microsoft Defender el ile nasıl dağıtılacağı açıklanır.
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
ms.openlocfilehash: a9d16cb82354bcb44e817de3207cb49de66dbf91
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873060"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-linux-manually"></a>Linux'ta Uç Nokta için Microsoft Defender el ile dağıtma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)


Bu makalede Linux'ta Uç Nokta için Microsoft Defender el ile nasıl dağıtılacağı açıklanmaktadır. Başarılı bir dağıtım için aşağıdaki görevlerin tümünün tamamlanması gerekir:

  - [Önkoşullar ve sistem gereksinimleri](#prerequisites-and-system-requirements)
  - [Linux yazılım deposunu yapılandırma](#configure-the-linux-software-repository)
    - [RHEL ve varyantları (CentOS, Fedora, Oracle Linux ve Amazon Linux 2)](#rhel-and-variants-centos-fedora-oracle-linux-and-amazon-linux-2)
    - [SLES ve çeşitlemeler](#sles-and-variants)
    - [Ubuntu ve Debian sistemleri](#ubuntu-and-debian-systems)
  - [Uygulama yüklemesi](#application-installation)
  - [Ekleme paketini indirme](#download-the-onboarding-package)
  - [İstemci yapılandırması](#client-configuration)

## <a name="prerequisites-and-system-requirements"></a>Önkoşullar ve sistem gereksinimleri

Başlamadan önce, geçerli yazılım sürümü için önkoşulların ve sistem gereksinimlerinin açıklaması için [bkz. Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md).

> [!WARNING]
> Ürün yüklemesinin ardından işletim sisteminizi yeni bir ana sürüme yükseltmek için ürünün yeniden yüklenmesi gerekir. Linux'ta mevcut Uç Nokta için [Defender'ı kaldırmanız](linux-resources.md#uninstall) , işletim sistemini yükseltmeniz ve ardından aşağıdaki adımları izleyerek Linux'ta Uç Nokta için Defender'ı yeniden yapılandırmanız gerekir.

## <a name="configure-the-linux-software-repository"></a>Linux yazılım deposunu yapılandırma

Linux'ta Uç Nokta için Defender aşağıdaki kanallardan birinden dağıtılabilir (aşağıda *[channel]* olarak belirtilir): *insider-fast*, *insider-slow* veya *prod*. Bu kanalların her biri bir Linux yazılım deposuna karşılık gelir. Cihazınızı bu depolardan birini kullanacak şekilde yapılandırma yönergeleri aşağıda verilmiştir.

Kanal seçimi, cihazınıza sunulan güncelleştirmelerin türünü ve sıklığını belirler. *Insider'ların hızlı* olduğu cihazlar, güncelleştirmeleri ve yeni özellikleri ilk alan cihazlardır ve daha sonra *insider'ların yavaş* ve son olarak *prod* tarafından takip edilir.

Yeni özellikleri önizlemek ve erken geri bildirim sağlamak için kuruluşunuzdaki bazı cihazları *insider hızlı veya insider yavaş* kullanacak şekilde yapılandırmanız önerilir.

> [!WARNING]
> İlk yüklemeden sonra kanalın değiştirilmesi için ürünün yeniden yüklenmesi gerekir. Ürün kanalını değiştirmek için: Mevcut paketi kaldırın, cihazınızı yeni kanalı kullanacak şekilde yeniden yapılandırın ve paketi yeni konumdan yüklemek için bu belgedeki adımları izleyin.

### <a name="rhel-and-variants-centos-fedora-oracle-linux-and-amazon-linux-2"></a>RHEL ve varyantları (CentOS, Fedora, Oracle Linux ve Amazon Linux 2)

- Henüz yüklenmediyse yükleyin `yum-utils` :

    ```bash
    sudo yum install yum-utils
    ```

  > [!NOTE]
  > Dağıtımınız ve sürümünüz ve altında `https://packages.microsoft.com/config/rhel/`bunun için en yakın girişi (ana, sonra ikincil) belirleyin.

    Paketi bulma konusunda size yardımcı olması için aşağıdaki tabloyu kullanın:

    <br>

    ****

    |Dağıtım & sürümü|Paket|
    |---|---|
    |RHEL/Centos/Oracle 8.0-8.5 için|<https://packages.microsoft.com/config/rhel/8/[channel].repo>|
    |RHEL/Centos/Oracle 7.2-7.9 & Amazon Linux 2 için |</azure/cognitive-services/speech-service/how-to-configure-rhel-centos-7>|
    <!--|RHEL/Centos 6.7-6.10 için|<https://packages.microsoft.com/config/rhel/6/[channel].repo>|-->
    |Fedora için 33|<https://packages.microsoft.com/config/fedora/33/prod.repo>|
    |Fedora için 34|<https://packages.microsoft.com/config/fedora/34/prod.repo>|

    Aşağıdaki komutlarda *[version]* ve *[channel]* sözcüklerini tanımladığınız bilgilerle değiştirin:


    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/[version]/[channel].repo
    ```

    > [!TIP]
    > *[version]* sürümü de dahil olmak üzere sistemle ilgili bilgileri tanımlamak için hostnamectl komutunu kullanın.

    Örneğin, CentOS 7 çalıştırıyorsanız ve *Dağıtım kanalından* Linux'ta Uç Nokta için Defender'ı dağıtmak istiyorsanız:

    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/7/prod.repo
    ```

    Alternatif olarak, seçilen cihazlardaki yeni özellikleri keşfetmek istiyorsanız, Linux'ta *insider* hızlı kanalına Uç Nokta için Microsoft Defender dağıtmak isteyebilirsiniz:

    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/7/insiders-fast.repo
    ```

- Microsoft GPG ortak anahtarını yükleyin:

    ```bash
    sudo rpm --import http://packages.microsoft.com/keys/microsoft.asc
    ```

### <a name="sles-and-variants"></a>SLES ve çeşitlemeler

> [!NOTE]
> Dağıtımınız ve sürümünüz ve altında `https://packages.microsoft.com/config/sles/`bunun için en yakın girişi (ana, sonra ikincil) belirleyin.

   Aşağıdaki komutlarda *[distro]* ve *[version]* sözcüklerini tanımladığınız bilgilerle değiştirin:

   ```bash
   sudo zypper addrepo -c -f -n microsoft-[channel] https://packages.microsoft.com/config/[distro]/[version]/[channel].repo
   ```

   > [!TIP]
   > Sürüm *[version]* dahil olmak üzere sistemle ilgili bilgileri tanımlamak için SPident komutunu kullanın.

   Örneğin, SLES 12 çalıştırıyorsanız ve *Uç Nokta için Microsoft Defender dağıtım* kanalından Linux'a dağıtmak istiyorsanız:

   ```bash
   sudo zypper addrepo -c -f -n microsoft-prod https://packages.microsoft.com/config/sles/12/prod.repo
   ```

- Microsoft GPG ortak anahtarını yükleyin:

    ```bash
    sudo rpm --import http://packages.microsoft.com/keys/microsoft.asc
    ```

### <a name="ubuntu-and-debian-systems"></a>Ubuntu ve Debian sistemleri

- Henüz yüklenmediyse yükleyin `curl` :

    ```bash
    sudo apt-get install curl
    ```

- Henüz yüklenmediyse yükleyin `libplist-utils` :

    ```bash
    sudo apt-get install libplist-utils
    ```

> [!NOTE]
> Dağıtımınız ve sürümünüz ve altında `https://packages.microsoft.com/config/[distro]/`bunun için en yakın girişi (ana, sonra ikincil) belirleyin.

   Aşağıdaki komutta *[distro]* ve *[version]* sözcüklerini tanımladığınız bilgilerle değiştirin:

   ```bash
    curl -o microsoft.list https://packages.microsoft.com/config/[distro]/[version]/[channel].list
   ```

   > [!TIP]
   > *[version]* sürümü de dahil olmak üzere sistemle ilgili bilgileri tanımlamak için hostnamectl komutunu kullanın.

   Örneğin, Ubuntu 18.04 çalıştırıyorsanız ve *dağıtım* kanalından Linux'ta Uç Nokta için Microsoft Defender dağıtmak istiyorsanız:

   ```bash
   curl -o microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list
   ```

- Depo yapılandırmasını yükleyin:

    ```bash
    sudo mv ./microsoft.list /etc/apt/sources.list.d/microsoft-[channel].list
    ```

    Örneğin, *üretim* kanalını seçtiyseniz:

    ```bash
    sudo mv ./microsoft.list /etc/apt/sources.list.d/microsoft-prod.list
    ```

- `gpg` Henüz yüklü değilse paketi yükleyin:

    ```bash
    sudo apt-get install gpg
    ```

  Kullanılamıyorsa `gpg` yükleyin `gnupg`.

    ```bash
    sudo apt-get install gnupg
    ```

- Microsoft GPG ortak anahtarını yükleyin:

    ```bash
    curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
    ```

- Henüz yoksa https sürücüsünü yükleyin:

    ```bash
    sudo apt-get install apt-transport-https
    ```

- Depo meta verilerini güncelleştirin:

    ```bash
    sudo apt-get update
    ```

## <a name="application-installation"></a>Uygulama yüklemesi

- RHEL ve varyantları (CentOS ve Oracle Linux):

    ```bash
    sudo yum install mdatp
    ```

    > [!NOTE]
    > Cihazınızda yapılandırılmış birden çok Microsoft deponuz varsa paketin yükleneceği depoya özgü olabilirsiniz. Aşağıdaki örnekte, bu cihazda depo kanalı da yapılandırılmışsa paketin `insiders-fast` kanaldan `production` nasıl yükleneceği gösterilmektedir. Cihazınızda birden çok Microsoft ürünü kullanıyorsanız bu durum oluşabilir. Sunucunuzun dağıtımına ve sürümüne bağlı olarak, depo diğer adı aşağıdaki örnekteki diğer addan farklı olabilir.

    ```bash
    # list all repositories
    yum repolist
    ```

    ```Output
    ...
    packages-microsoft-com-prod               packages-microsoft-com-prod        316
    packages-microsoft-com-prod-insiders-fast packages-microsoft-com-prod-ins      2
    ...
    ```

    ```bash
    # install the package from the production repository
    sudo yum --enablerepo=packages-microsoft-com-prod install mdatp
    ```

- SLES ve varyantlar:

    ```bash
    sudo zypper install mdatp
    ```

    > [!NOTE]
    > Cihazınızda yapılandırılmış birden çok Microsoft deponuz varsa paketin yükleneceği depoya özgü olabilirsiniz. Aşağıdaki örnekte, bu cihazda depo kanalı da yapılandırılmışsa paketin `insiders-fast` kanaldan `production` nasıl yükleneceği gösterilmektedir. Cihazınızda birden çok Microsoft ürünü kullanıyorsanız bu durum oluşabilir.

    ```bash
    zypper repos
    ```

    ```Output
    ...
    #  | Alias | Name | ...
    XX | packages-microsoft-com-insiders-fast | microsoft-insiders-fast | ...
    XX | packages-microsoft-com-prod | microsoft-prod | ...
    ...

    ```

    ```bash
    sudo zypper install packages-microsoft-com-prod:mdatp
    ```

- Ubuntu ve Debian sistemi:

    ```bash
    sudo apt-get install mdatp
    ```

    > [!NOTE]
    > Cihazınızda yapılandırılmış birden çok Microsoft deponuz varsa paketin yükleneceği depoya özgü olabilirsiniz. Aşağıdaki örnekte, bu cihazda depo kanalı da yapılandırılmışsa paketin `insiders-fast` kanaldan `production` nasıl yükleneceği gösterilmektedir. Cihazınızda birden çok Microsoft ürünü kullanıyorsanız bu durum oluşabilir.

    ```bash
    cat /etc/apt/sources.list.d/*
    ```

    ```Output
    deb [arch=arm64,armhf,amd64] https://packages.microsoft.com/config/ubuntu/18.04/prod insiders-fast main
    deb [arch=amd64] https://packages.microsoft.com/config/ubuntu/18.04/prod bionic main
    ```

    ```bash
    sudo apt -t bionic install mdatp
    ```

## <a name="download-the-onboarding-package"></a>Ekleme paketini indirme

Ekleme paketini Microsoft 365 Defender portalından indirin.

> [!IMPORTANT]
> Bu adımı kaçırırsanız, yürütülen herhangi bir komut ürünün lisanssız olduğunu belirten bir uyarı iletisi gösterir. `mdatp health` Ayrıca komutu değerini `false`döndürür.

1. Microsoft 365 Defender portalında **Ayarlar > Uç Noktaları > Cihaz yönetimi > Ekleme'ye** gidin.
2. İlk açılan menüde işletim sistemi olarak **Linux Server'ı** seçin. İkinci açılan menüde dağıtım yöntemi olarak **Yerel Betik'i** seçin.
3. **Ekleme paketini indir'i** seçin. Dosyayı WindowsDefenderATPOnboardingPackage.zip olarak kaydedin.

   :::image type="content" source="images/portal-onboarding-linux.png" alt-text="Microsoft 365 Defender portalında ekleme paketi indirme" lightbox="images/portal-onboarding-linux.png":::

4. Komut isteminden dosyaya sahip olduğunuzu doğrulayın ve arşivin içeriğini ayıklayın:

    ```bash
    ls -l
    ```

    ```Output
    total 8
    -rw-r--r-- 1 test  staff  5752 Feb 18 11:22 WindowsDefenderATPOnboardingPackage.zip
    ```

    ```bash
    unzip WindowsDefenderATPOnboardingPackage.zip
    ```

    ```Output
    Archive:  WindowsDefenderATPOnboardingPackage.zip
    inflating: MicrosoftDefenderATPOnboardingLinuxServer.py
    ```

## <a name="client-configuration"></a>İstemci yapılandırması

1. MicrosoftDefenderATPOnboardingLinuxServer.py hedef cihaza kopyalayın.

    > [!NOTE]
    > Başlangıçta istemci cihazı bir kuruluşla ilişkilendirilmemiştir ve *orgId* özniteliği boş olur.

    ```bash
    mdatp health --field org_id
    ```

2. MicrosoftDefenderATPOnboardingLinuxServer.py çalıştırın.

    > [!NOTE]
    > Bu komutu çalıştırmak için, disto ve sürüme bağlı olarak cihaza sahip `python`  olmanız veya `python3` yüklemeniz gerekir. Gerekirse bkz. [Linux'ta Python Yükleme için Adım Adım Yönergeler](https://opensource.com/article/20/4/install-python-linux).
    
    RHEL 8.x veya Ubuntu 20.04 veya üzerini çalıştırıyorsanız kullanmanız `python3`gerekir.

    ```bash
    sudo python3 MicrosoftDefenderATPOnboardingLinuxServer.py
    ```

    Diğer dağıtımlar ve sürümler için kullanmanız `python`gerekir.
    
    ```bash
    sudo python MicrosoftDefenderATPOnboardingLinuxServer.py
    ```
    
3. Cihazın artık kuruluşunuzla ilişkilendirildiğini ve geçerli bir kuruluş tanımlayıcısı bildirdiğini doğrulayın:

    ```bash
    mdatp health --field org_id
    ```

4. Aşağıdaki komutu çalıştırarak ürünün sistem durumunu denetleyin. Dönüş değeri `1` , ürünün beklendiği gibi çalıştığını belirtir:

    ```bash
    mdatp health --field healthy
    ```

    > [!IMPORTANT]
    > Ürün ilk kez başlatıldığında en son kötü amaçlı yazılımdan koruma tanımlarını indirir. Bu işlem, ağ bağlantısına bağlı olarak birkaç dakika kadar sürebilir. Bu süre boyunca yukarıdaki komut değerini `false`döndürür. Tanım güncelleştirmesinin durumunu denetlemek için aşağıdaki komutu kullanabilirsiniz:
    >
    > ```bash
    > mdatp health --field definitions_status
    > ```
    >
    > İlk yüklemeyi tamamladıktan sonra bir ara sunucu yapılandırmanız gerekebileceğini lütfen unutmayın. Bkz [. Linux'ta Uç Nokta için Defender'ı statik proxy bulma için yapılandırma: Yükleme sonrası yapılandırma](linux-static-proxy-configuration.md#post-installation-configuration).

5. Cihazın düzgün şekilde eklendiğini ve hizmete bildirildiğini doğrulamak için bir AV algılama testi çalıştırın. Yeni eklenen cihazda aşağıdaki adımları gerçekleştirin:

    - Gerçek zamanlı korumanın etkinleştirildiğinden emin olun (aşağıdaki komutu çalıştırmanın `1` sonucu olarak belirtilir):

        ```bash
        mdatp health --field real_time_protection_enabled
        ```
        
      Etkinleştirilmemişse aşağıdaki komutu yürütür:
      
       ```bash
        mdatp config real-time-protection --value enabled
        ```

    - Bir Terminal penceresi açın ve aşağıdaki komutu yürütür:

        ``` bash
        curl -o /tmp/eicar.com.txt https://www.eicar.org/download/eicar.com.txt
        ```

    - Dosya Linux'ta Uç Nokta için Defender tarafından karantinaya alınmış olmalıdır. Algılanan tüm tehditleri listelemek için aşağıdaki komutu kullanın:

        ```bash
        mdatp threat list
        ```

6. Cihazın düzgün şekilde eklendiğini ve hizmete bildirildiğini doğrulamak için bir EDR algılama testi çalıştırın ve algılama simülasyonu yapın. Yeni eklenen cihazda aşağıdaki adımları gerçekleştirin:

    - Eklenen Linux sunucusunun Microsoft 365 Defender görüntülendiğini doğrulayın. Makinenin ilk eklemesi buysa, görünmesi 20 dakika kadar sürebilir.

    - [Betik dosyasını](https://aka.ms/LinuxDIY) indirip ekli bir Linux sunucusuna ayıklayın ve aşağıdaki komutu çalıştırın:`./mde_linux_edr_diy.sh`

    - Birkaç dakika sonra, Microsoft 365 Defender içinde bir algılama tetiklenmelidir.

    - Uyarı ayrıntılarına, makine zaman çizelgesine bakın ve tipik araştırma adımlarınızı gerçekleştirin.

## <a name="installer-script"></a>Yükleyici betiği

Alternatif olarak, [genel GitHub depomuzda](https://github.com/microsoft/mdatp-xplat/) sağlanan otomatik [yükleyici bash betiğini](https://github.com/microsoft/mdatp-xplat/blob/master/linux/installation/mde_installer.sh) kullanabilirsiniz.
Betik dağıtımı ve sürümü tanımlar, doğru depo seçimini basitleştirir, cihazı en son paketi çekecek şekilde ayarlar ve ürün yükleme ve ekleme adımlarını birleştirir.

```bash
> ./mde_installer.sh --help
usage: basename ./mde_installer.sh [OPTIONS]
Options:
-c|--channel      specify the channel from which you want to install. Default: insiders-fast
-i|--install      install the product
-r|--remove       remove the product
-u|--upgrade      upgrade the existing product
-o|--onboard      onboard/offboard the product with <onboarding_script>
-p|--passive-mode set EPP to passive mode
-t|--tag          set a tag by declaring <name> and <value>. ex: -t GROUP Coders
-m|--min_req      enforce minimum requirements
-w|--clean        remove repo from package manager for a specific channel
-v|--version      print out script version
-h|--help         display help
```

Daha fazla bilgi [için buraya bakın](https://github.com/microsoft/mdatp-xplat/tree/master/linux/installation).

## <a name="log-installation-issues"></a>Günlük yükleme sorunları

Bir hata oluştuğunda yükleyici tarafından oluşturulan otomatik olarak oluşturulan günlüğü bulma hakkında daha fazla bilgi için bkz. [Günlük yükleme sorunları](linux-resources.md#log-installation-issues) .

## <a name="how-to-migrate-from-insiders-fast-to-production-channel"></a>Insiders-Fast'dan Üretim kanalına geçiş

1. Linux'ta Uç Nokta için Defender'ın "Insider-Hızlı kanal" sürümünü kaldırın.

    ```bash
    sudo yum remove mdatp
    ```

1. Linux Insiders-Fast deposunda Uç Nokta için Defender'ı devre dışı bırakma

    ```bash
    sudo yum repolist
    ```

    > [!NOTE]
    > Çıkışta "packages-microsoft-com-fast-prod" gösterilmelidir.

    ```bash
    sudo yum-config-manager --disable packages-microsoft-com-fast-prod
    ```

1. "Üretim kanalını" kullanarak Linux'ta Uç Nokta için Microsoft Defender yeniden dağıtın.

## <a name="uninstallation"></a>Kaldırma

Linux'ta Uç Nokta için Defender'ı istemci cihazlarından kaldırma hakkında ayrıntılı bilgi için bkz. [Kaldırma](linux-resources.md#uninstall) .

## <a name="see-also"></a>Ayrıca bkz.

- [Sistem durumu sorunlarını araştırın](health-status.md)
