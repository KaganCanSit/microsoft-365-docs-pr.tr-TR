---
title: Linux'ta Uç Nokta için Microsoft Defender'ı el ile dağıtma
ms.reviewer: ''
description: Linux'ta Uç Nokta için Microsoft Defender'ın komut satırına el ile nasıl dağıtın açıklanır.
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
ms.openlocfilehash: da05d702a2cb074ece2fec74371e7b5f560cb1ed
ms.sourcegitcommit: babc2dad1c0e08a9237dbe4956ffd21c0214db83
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2022
ms.locfileid: "63014338"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-linux-manually"></a>Linux'ta Uç Nokta için Microsoft Defender'ı el ile dağıtma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)


Bu makalede Linux'ta Uç Nokta için Microsoft Defender'ın el ile nasıl dağıt olduğu açıklanmıştır. Başarılı bir dağıtım için aşağıdaki görevlerin tamamlanmasını gerekir:

  - [Önkoşullar ve sistem gereksinimleri](#prerequisites-and-system-requirements)
  - [Linux yazılım deposunu yapılandırma](#configure-the-linux-software-repository)
    - [RHEL ve çeşitlemeler (CentOS, Fedora, Oracle Linux ve Amazon Linux 2)](#rhel-and-variants-centos-fedora-oracle-linux-and-amazon-linux-2)
    - [SLES ve çeşitlemeler](#sles-and-variants)
    - [Ubuntu ve Debian sistemleri](#ubuntu-and-debian-systems)
  - [Uygulama yüklemesi](#application-installation)
  - [Ekleme paketini indirin](#download-the-onboarding-package)
  - [İstemci yapılandırması](#client-configuration)

## <a name="prerequisites-and-system-requirements"></a>Önkoşullar ve sistem gereksinimleri

Başlamadan önce, geçerli yazılım sürümünün [önkoşullarının](microsoft-defender-endpoint-linux.md) ve sistem gereksinimlerinin açıklaması için bkz. Linux'ta Uç Nokta için Microsoft Defender.

> [!WARNING]
> Ürün yüklemesi sonrasında işletim sisteminizi yeni bir ana sürüme yükseltmek için ürünün yeniden yüklenmesi gerekir. Aşağıdaki adımları takip [edin ve](linux-resources.md#uninstall) Linux'ta Uç Nokta için Defender'ı kaldırmanız, işletim sistemini yükseltmeniz ve ardından Linux'ta Uç Nokta için Defender'ı yeniden yapılandırmanız gerekir.

## <a name="configure-the-linux-software-repository"></a>Linux yazılım deposunu yapılandırma

Linux'ta Uç Nokta için Defender aşağıdaki kanallardan biri (*[kanal]* olarak açıklanmıştır) *dağıtılabilir*: *insider hızlı*, *insider-slow* veya prod. Bu kanalların her biri bir Linux yazılım deposuna karşılık geldi. Cihazınızı bu depolardan birini kullanmak üzere yapılandırma yönergeleri aşağıda verilmiştir.

Kanalın seçimi, cihazınıza sunulan güncelleştirmelerin türünü ve sıklığını belirler. Insider *hızlı olan cihazlar,* güncelleştirmeleri ve yeni özellikleri alan ilk cihazlardır ve bunu daha sonra *Insider yavaş* ve son olarak *prod takip edin*.

Yeni özelliklerin önizlemesini görüntülemek ve erken geri bildirim sağlamak için, kuruluş içindeki bazı cihazları *Insider hızlı veya insider-slow* kullanmaya yönelik olarak *yapılandırmanız önerilir*.

> [!WARNING]
> İlk yüklemeden sonra kanalı değiştirmek için ürünün yeniden yüklenmesi gerekir. Ürün kanalını değiştirmek için: var olan paketi kaldırın, cihazınızı yeni kanalı kullanmak üzere yeniden yapılandırın ve paketi yeni konumdan yüklemek için bu belge'de yer alan adımları izleyin.

### <a name="rhel-and-variants-centos-fedora-oracle-linux-and-amazon-linux-2"></a>RHEL ve çeşitlemeler (CentOS, Fedora, Oracle Linux ve Amazon Linux 2)

- Henüz `yum-utils` yüklenmemişse yükleyin:

    ```bash
    sudo yum install yum-utils
    ```

  > [!NOTE]
  > dağıtım ve sürümünüzdür ve onun için en yakın girdiyi (ana, küçük olan) belirlemesi için 'nin altında bu girdiyi seçin `https://packages.microsoft.com/config/rhel/`.

    Paketi bulmada size yol göstermede yardımcı olmak için aşağıdaki tabloyu kullanın:

    <br>

    ****

    |Bir & dağıtım|Paket|
    |---|---|
    |RHEL/Centos/Oracle 8.0-8.5 için|<https://packages.microsoft.com/config/rhel/8/[channel].repo>|
    |Amazon Linux 2'de RHEL/Centos/Oracle 7.2-7.9 & için |<https://packages.microsoft.com/config/rhel/7/[channel].repo>|
    |RHEL/Centos için 6.7-6.10|<https://packages.microsoft.com/config/rhel/6/[channel].repo>|
    |Fedora 33 için|<https://packages.microsoft.com/config/fedora/33/prod.repo>|
    |Fedora 34 için|<https://packages.microsoft.com/config/fedora/34/prod.repo>|

    Aşağıdaki komutlarda, *[sürüm] ve* *[kanal]* ifadelerini tanımladık bilgilerle değiştirin:


    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/[version]/[channel].repo
    ```

    > [!TIP]
    > Sürüm [sürüm] de içinde olmak üzere sistemle ilgili bilgileri tanımlamak için hostnamectl *komutunu kullanın*.

    Örneğin, CentOS 7 kullanıyorsanız ve *prod* kanalından Linux'ta Uç Nokta için Defender'ı dağıtmak istiyorsanız:

    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/7/prod.repo
    ```

    Seçili cihazlarda yeni özellikleri keşfetmek isterseniz, Linux'ta Uç Nokta için Microsoft Defender'ı Insider hızlı kanalına dağıtmak *da istiyor* da olabilir:

    ```bash
    sudo yum-config-manager --add-repo=https://packages.microsoft.com/config/rhel/7/insiders-fast.repo
    ```

- Microsoft GPG ortak anahtarını yükleme:

    ```bash
    sudo rpm --import http://packages.microsoft.com/keys/microsoft.asc
    ```

### <a name="sles-and-variants"></a>SLES ve çeşitlemeler

> [!NOTE]
> dağıtım ve sürümünüzdür ve onun için en yakın girdiyi (ana, küçük olan) belirlemesi için 'nin altında bu girdiyi seçin `https://packages.microsoft.com/config/sles/`.

   Aşağıdaki komutlarda, *[distro]* ve *[version]* ifadelerini tanımdığer bilgilerle değiştirin:

   ```bash
   sudo zypper addrepo -c -f -n microsoft-[channel] https://packages.microsoft.com/config/[distro]/[version]/[channel].repo
   ```

   > [!TIP]
   > Sürüm [sürüm] de içinde olmak üzere sistemle ilgili bilgileri tanımlamak için SPident *komutunu kullanın*.

   Örneğin, SLES 12 kullanıyorsanız ve *prod* kanalından Linux'ta Uç Nokta için Microsoft Defender'ı dağıtmak isterseniz:

   ```bash
   sudo zypper addrepo -c -f -n microsoft-prod https://packages.microsoft.com/config/sles/12/prod.repo
   ```

- Microsoft GPG ortak anahtarını yükleme:

    ```bash
    sudo rpm --import http://packages.microsoft.com/keys/microsoft.asc
    ```

### <a name="ubuntu-and-debian-systems"></a>Ubuntu ve Debian sistemleri

- Henüz `curl` yüklenmemişse yükleyin:

    ```bash
    sudo apt-get install curl
    ```

- Henüz `libplist-utils` yüklenmemişse yükleyin:

    ```bash
    sudo apt-get install libplist-utils
    ```

> [!NOTE]
> dağıtım ve sürümünüzdür ve onun için en yakın girdiyi (ana, küçük olan) belirlemesi için 'nin altında bu girdiyi seçin `https://packages.microsoft.com/config/[distro]/`.

   Aşağıdaki komutta, *[distro]* ve *[version]* ifadelerini tanımdığer bilgilerle değiştirin:

   ```bash
    curl -o microsoft.list https://packages.microsoft.com/config/[distro]/[version]/[channel].list
   ```

   > [!TIP]
   > Sürüm [sürüm] de içinde olmak üzere sistemle ilgili bilgileri tanımlamak için hostnamectl *komutunu kullanın*.

   Örneğin, Ubuntu 18.04 kullanıyorsanız ve *prod* kanalından Linux'ta Uç Nokta için Microsoft Defender'ı dağıtmak isterseniz:

   ```bash
   curl -o microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list
   ```

- Depolama yapılandırmasını yükleme:

    ```bash
    sudo mv ./microsoft.list /etc/apt/sources.list.d/microsoft-[channel].list
    ```

    Örneğin, prod *kanalı seçtiysanız* :

    ```bash
    sudo mv ./microsoft.list /etc/apt/sources.list.d/microsoft-prod.list
    ```

- `gpg` Paket henüz yüklenmemişse yükleyin:

    ```bash
    sudo apt-get install gpg
    ```

  Kullanılamıyorsa `gpg` yükleyin `gnupg`.

    ```bash
    sudo apt-get install gnupg
    ```

- Microsoft GPG ortak anahtarını yükleme:

    ```bash
    curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
    ```

- Henüz mevcut değilken https sürücüsünü yükleyin:

    ```bash
    sudo apt-get install apt-transport-https
    ```

- Depo meta verilerini güncelleştirme:

    ```bash
    sudo apt-get update
    ```

## <a name="application-installation"></a>Uygulama yüklemesi

- RHEL ve çeşitlemeler (CentOS ve Oracle Linux):

    ```bash
    sudo yum install mdatp
    ```

    > [!NOTE]
    > Aygıtınızda birden çok Microsoft deposu yapılandırılmışsa, paketin hangi depodan yükll üzere belirli bir depo olduğu belli olabilir. Aşağıdaki örnekte, bu cihazda da yapılandırılmış `production` depolama kanalınız `insiders-fast` varsa, paketin kanaldan nasıl yük yüklemeniz olduğu gösterir. Bu durum, aygıtınızda birden çok Microsoft ürünü kullanıyorsanız olabilir. Dağıtıma ve sunucu sürümüne bağlı olarak, depo diğer adı aşağıdaki örnekte yer alan diğer addan farklı olabilir.

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

- SLES ve çeşitlemeler:

    ```bash
    sudo zypper install mdatp
    ```

    > [!NOTE]
    > Aygıtınızda birden çok Microsoft deposu yapılandırılmışsa, paketin hangi depodan yükll üzere belirli bir depo olduğu belli olabilir. Aşağıdaki örnekte, bu cihazda da yapılandırılmış `production` depolama kanalınız `insiders-fast` varsa, paketin kanaldan nasıl yük yüklemeniz olduğu gösterir. Bu durum, aygıtınızda birden çok Microsoft ürünü kullanıyorsanız olabilir.

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
    > Aygıtınızda birden çok Microsoft deposu yapılandırılmışsa, paketin hangi depodan yükll üzere belirli bir depo olduğu belli olabilir. Aşağıdaki örnekte, bu cihazda da yapılandırılmış `production` depolama kanalınız `insiders-fast` varsa, paketin kanaldan nasıl yük yüklemeniz olduğu gösterir. Bu durum, aygıtınızda birden çok Microsoft ürünü kullanıyorsanız olabilir.

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

## <a name="download-the-onboarding-package"></a>Ekleme paketini indirin

Ekleme paketini portaldan Microsoft 365 Defender indirin.

> [!IMPORTANT]
> Bu adımı kaçırırsanız, yürütülen herhangi bir komut ürünün lisanssız olduğunu belirten bir uyarı iletisi görüntüler. Komut, `mdatp health` 'ın değerini de döndürür `false`.

1. Microsoft 365 Defender Portalında, Ayarlar > **Uç Noktaları ve Cihaz > Ekleme'> gidin**.
2. İlk açılan menüde işletim sistemi olarak **Linux Server'ı** seçin. İkinci açılan menüde dağıtım yöntemi olarak **Yerel Betik'i** seçin.
3. Ekleme **paketini indir'i seçin**. Dosyayı farklı bir WindowsDefenderATPOnboardingPackage.zip.

    ![Microsoft 365 Defender portalın ekran görüntüsü.](images/portal-onboarding-linux.png)

4. Komut isteminden, dosyanın size ait olduğunu doğrulayın ve arşivin içeriğini ayıkla:

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

1. Diğer MicrosoftDefenderATPOnboardingLinuxServer.py hedef cihaza kopyalayın.

    > [!NOTE]
    > Başlangıçta istemci cihazı kuruluşla ilişkilendirilmiş değildir ve *orgId* özniteliği boştur.

    ```bash
    mdatp health --field org_id
    ```

2. Diğer MicrosoftDefenderATPOnboardingLinuxServer.py.

    > [!NOTE]
    > Bu komutu çalıştırmak için, disto ve `python` `python3` sürüme bağlı olarak cihaza yüklenmiş veya yüklenmiş olması gerekir. Gerekirse bkz. [Linux'ta Python'i yüklemek için adım adım yönerge](https://opensource.com/article/20/4/install-python-linux).
    
    RHEL 8.x veya Ubuntu 20.04 veya daha yüksek bir değer kullanıyorsanız, 'ı kullansanız gerekir `python3`.

    ```bash
    sudo python3 MicrosoftDefenderATPOnboardingLinuxServer.py
    ```

    Diğer girişler ve sürümler için ' kullanın `python`.
    
    ```bash
    sudo python MicrosoftDefenderATPOnboardingLinuxServer.py
    ```
    
3. Cihazın şimdi organizasyonuyla ilişkili olduğunu doğrulayın ve geçerli bir kuruluş tanımlayıcısı rapor edin:

    ```bash
    mdatp health --field org_id
    ```

4. Aşağıdaki komutu çalıştırarak ürünün durumunu kontrol edin. Ürünün beklendiği gibi `1` ilerlemektedir. Sonuç değeri:

    ```bash
    mdatp health --field healthy
    ```

    > [!IMPORTANT]
    > Ürün ilk kez başlatıldığında, en son kötü amaçlı yazılımdan koruma tanımlarını indirir. Bu, ağ bağlantısına bağlı olarak birkaç dakika sürebilir. Bu sırada yukarıdaki komut bir değeri döndürür `false`. Aşağıdaki komutu kullanarak tanım güncelleştirmesini durumunu kontrol edin:
    >
    > ```bash
    > mdatp health --field definitions_status
    > ```
    >
    > İlk yükleme tamamladıktan sonra bir proxy yapılandırmanız gerekey olduğunu lütfen unutmayın. Statik [proxy bulma için Linux'ta Uç Nokta için Defender'ı Yapılandırma: Yükleme sonrası yapılandırma](linux-static-proxy-configuration.md#post-installation-configuration).

5. Cihazın düzgün bir şekilde işe alımlı olduğunu ve hizmete rapor olduğunu doğrulamak için AV algılama testini çalıştırın. Yeni eklenen cihazda aşağıdaki adımları uygulayın:

    - Gerçek zamanlı korumanın etkinleştirildiğinden emin olun (aşağıdaki komutun `1` çalıştırması sonucunda:

        ```bash
        mdatp health --field real_time_protection_enabled
        ```
        
      Etkin değilse aşağıdaki komutu yürütün:
      
       ```bash
        mdatp config real-time-protection --value enabled
        ```

    - Terminal penceresini açın ve aşağıdaki komutu yürütün:

        ``` bash
        curl -o /tmp/eicar.com.txt https://www.eicar.org/download/eicar.com.txt
        ```

    - Dosya Linux'ta Uç Nokta için Defender tarafından karantinaya alınmış olmalıdır. Algılanan tüm tehditleri listeleyen aşağıdaki komutu kullanın:

        ```bash
        mdatp threat list
        ```

6. Cihazın düzgün EDR ve hizmete bildirilmiş olduğunu doğrulamak için, EDR algılama testini çalıştırın ve algılamayı benzetimini yap. Yeni eklenen cihazda aşağıdaki adımları uygulayın:

    - Yerleşik Linux sunucusunun Linux'ta görüntülendiğinden Microsoft 365 Defender. Bu makineye ilk kez geliyorsa, görüntülenene kadar 20 dakika kadar sürebilir.

    - Betik dosyasını [yerleşik bir](https://aka.ms/LinuxDIY) Linux sunucusuna indirip ayık edin ve aşağıdaki komutu çalıştırın: `./mde_linux_edr_diy.sh`

    - Birkaç dakika sonra, iki alan içinde bir algılama Microsoft 365 Defender.

    - Uyarı ayrıntılarına, makine zaman çizelgesine bakın ve tipik araştırma adımlarınızı gerçekleştirin.

## <a name="installer-script"></a>Yükleyici betiği

Alternatif olarak, genel hizmet depomuzda [sağlanan otomatik](https://github.com/microsoft/mdatp-xplat/blob/master/linux/installation/mde_installer.sh) yükleyici bash [betiği GitHub kullanabilirsiniz](https://github.com/microsoft/mdatp-xplat/).
Betikte dağıtım ve sürüm tanımlanıyor, doğru depolama alanı seçimi basitleştirildi, en son paketi çekmek için cihaz ayarlanıyor, ürün yükleme ve ekleme adımları birleştirildi.

```bash
❯ ./mde_installer.sh --help
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

Buradan daha fazlasını [okuyun](https://github.com/microsoft/mdatp-xplat/tree/master/linux/installation).

## <a name="log-installation-issues"></a>Günlük yükleme sorunları

Hata [oluştuğunda](linux-resources.md#log-installation-issues) yükleyici tarafından oluşturulan otomatik günlüğü bulma hakkında daha fazla bilgi için bkz. Günlük yükleme sorunları.

## <a name="how-to-migrate-from-insiders-fast-to-production-channel"></a>Insiders-Fast kanalından Üretim kanalına geçiş

1. Linux'ta Endpoint için Defender'ın "Insider Hızlı kanalı" sürümünü kaldırın.

    ```bash
    sudo yum remove mdatp
    ```

1. Linux Insiders-Fast repo'da Uç Nokta için Defender'ı devre dışı bırakma

    ```bash
    sudo yum repolist
    ```

    > [!NOTE]
    > Çıkışta "packages-microsoft-com-fast-prod" göster gerekir.

    ```bash
    sudo yum-config-manager --disable packages-microsoft-com-fast-prod
    ```

1. "Üretim kanalını" kullanarak Linux'ta Uç Nokta için Microsoft Defender'ı yeniden dağıtım.

## <a name="uninstallation"></a>Kaldırma

İstemci [cihazlarından](linux-resources.md#uninstall) Linux'ta Uç Nokta için Defender'ı kaldırma hakkında ayrıntılar için bkz. Kaldırma.

## <a name="see-also"></a>Ayrıca bkz.

- [Aracı durumu sorunlarını araştırma](health-status.md)
