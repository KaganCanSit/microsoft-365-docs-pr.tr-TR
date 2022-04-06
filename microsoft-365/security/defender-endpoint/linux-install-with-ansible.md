---
title: Linux'Uç Nokta için Microsoft Defender Ansible ile dağıtım
ms.reviewer: ''
description: Ansible kullanarak Linux Uç Nokta için Microsoft Defender'i nasıl dağıtın açıklaması vardır.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, linux, yükleme, dağıtma, kaldırma, kaldırılabilir, ansible, linux, redhat, ubuntu, debian, sles, suse, centos, fedora, amazon linux 2
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
ms.openlocfilehash: 57f0687fce422f26b76fc8b98a06ce0566f90f60
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476081"
---
# <a name="deploy-microsoft-defender-for-endpoint-on-linux-with-ansible"></a>Linux'Uç Nokta için Microsoft Defender Ansible ile dağıtım

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Bu makalede, Ansible kullanarak Linux'ta Uç Nokta için Defender'ın nasıl dağıt olduğu açıklanmıştır. Başarılı bir dağıtım için aşağıdaki görevlerin tamamlanmasını gerekir:

- [Ekleme paketini indirin](#download-the-onboarding-package)
- [Ansible YAML dosyaları oluşturma](#create-ansible-yaml-files)
- [Dağıtım](#deployment)
- [Başvurular](#references)

## <a name="prerequisites-and-system-requirements"></a>Önkoşullar ve sistem gereksinimleri

Başlamadan önce, geçerli yazılım sürümünün [önkoşullarının](microsoft-defender-endpoint-linux.md) ve sistem gereksinimlerinin açıklaması için Linux'ta uç nokta için ana Defender sayfasına bakın.

Buna ek olarak, Ansible dağıtımı için, Ansible yönetim görevlerini biliyor, Ansible yapılandırılmış olmalı ve çalışma kitaplarını ve görevlerin nasıl dağıt dağıtıldığından emin omalısınız. Ansible'da aynı görevi tamamlamak için birçok yol vardır. Bu yönergelerde, paketin dağıtımına yardımcı olmak için *apt* ve *unarchive* gibi desteklenen Ansible modüllerinin kullanılabilirliği varsayıldı. Organizasyonunız farklı bir iş akışı kullanabilir. Ayrıntılar için [, Ansible belgelerine](https://docs.ansible.com/) bakın.

- Ansible'ın en az bir bilgisayara yüklenmiş olması gerekir (Ansible bunu denetim düğümü olarak arar).
- SSH' nin denetim düğümüyle tüm yönetilen düğümler (üzerinde Uç Nokta için Defender yüklü olacak cihazlar) arasında bir yönetici hesabı için yapılandırılması gerekir ve ortak anahtar kimlik doğrulamasıyla yapılandırılması önerilir.
- Aşağıdaki yazılımlar tüm yönetilen düğümlere yüklenmeli:
  - kıvrık
  - python-apt

- Tüm yönetilen düğümlerin ya da ilgili dosyada aşağıdaki biçimde `/etc/ansible/hosts` listelenmiş olması gerekir:

    ```bash
    [servers]
    host1 ansible_ssh_host=10.171.134.39
    host2 ansible_ssh_host=51.143.50.51
    ```

- Ping testi:

    ```bash
    ansible -m ping all
    ```

## <a name="download-the-onboarding-package"></a>Ekleme paketini indirin

Kullanıcı portalı üzerinden ekleme Microsoft 365 Defender indirin:

1. Uygulama Microsoft 365 Defender, Uç Noktaları **Ayarlar > Ve Cihaz yönetimi >'e > gidin**.
2. İlk açılan menüde işletim sistemi olarak **Linux Server'ı** seçin. İkinci açılan menüde dağıtım yöntemi olarak **Tercih ettiğiniz Linux yapılandırma yönetim aracı'nı** seçin.
3. Ekleme **paketini indir'i seçin**. Dosyayı farklı bir WindowsDefenderATPOnboardingPackage.zip.

   :::image type="content" source="images/portal-onboarding-linux-2.png" alt-text="Ekleme paketini indir seçeneği" lightbox="images/portal-onboarding-linux-2.png":::

4. Komut isteminden, dosyanın size ait olduğunu doğrulayın. Arşivin içeriğini ayıklama:

    ```bash
    ls -l
    ```
    ```Output
    total 8
    -rw-r--r-- 1 test  staff  4984 Feb 18 11:22 WindowsDefenderATPOnboardingPackage.zip
    ```
    ```bash
    unzip WindowsDefenderATPOnboardingPackage.zip
    ```
    ```Output
    Archive:  WindowsDefenderATPOnboardingPackage.zip
    inflating: mdatp_onboard.json
    ```

## <a name="create-ansible-yaml-files"></a>Ansible YAML dosyaları oluşturma

Bir çalışma kitabına veya göreve katkıda bulunan alt görev veya rol dosyaları oluşturun.

- Ekleme görevini oluşturun: `onboarding_setup.yml`

    ```bash
    - name: Create MDATP directories
      file:
        path: /etc/opt/microsoft/mdatp/
        recurse: true
        state: directory
        mode: 0755
        owner: root
        group: root

    - name: Register mdatp_onboard.json
      stat:
        path: /etc/opt/microsoft/mdatp/mdatp_onboard.json
      register: mdatp_onboard

    - name: Extract WindowsDefenderATPOnboardingPackage.zip into /etc/opt/microsoft/mdatp
      unarchive:
        src: WindowsDefenderATPOnboardingPackage.zip
        dest: /etc/opt/microsoft/mdatp
        mode: 0600
        owner: root
        group: root
      when: not mdatp_onboard.stat.exists
    ```

- Uç nokta havuzu ve anahtarı için Defender'ı ekleyin: `add_apt_repo.yml`

    Linux'ta Uç Nokta için Defender aşağıdaki kanallardan biri (*[kanal]* olarak açıklanmıştır) *dağıtılabilir*: *insider hızlı*, *insider-slow* veya prod. Bu kanalların her biri bir Linux yazılım deposuna karşılık geldi.

    Kanalın seçimi, cihazınıza sunulan güncelleştirmelerin türünü ve sıklığını belirler. Insider *hızlı olan cihazlar,* güncelleştirmeleri ve yeni özellikleri alan ilk cihazlardır ve bunu daha sonra *Insider yavaş* ve son olarak *prod takip edin*.

    Yeni özelliklerin önizlemesini görüntülemek ve erken geri bildirim sağlamak için, kuruluş içindeki bazı cihazları *Insider hızlı veya insider-slow* kullanmaya yönelik olarak *yapılandırmanız önerilir*.

    > [!WARNING]
    > İlk yüklemeden sonra kanalı değiştirmek için ürünün yeniden yüklenmesi gerekir. Ürün kanalını değiştirmek için: var olan paketi kaldırın, cihazınızı yeni kanalı kullanmak üzere yeniden yapılandırın ve paketi yeni konumdan yüklemek için bu belge'de yer alan adımları izleyin.

    Dağıtımınızı ve sürümünizi not edin ve altında ona en yakın girişi tanımlayabilirsiniz `https://packages.microsoft.com/config/[distro]/`.

    Aşağıdaki komutlarda, *[distro]* ve *[version]* ifadelerini tanımdığer bilgilerle değiştirin.

    > [!NOTE]
    > Oracle Linux ve Amazon Linux 2'de, *[distro]* ifadesini "rhel" ile değiştirin.

  ```bash
  - name: Add Microsoft APT key
    apt_key:
      url: https://packages.microsoft.com/keys/microsoft.asc
      state: present
    when: ansible_os_family == "Debian"

  - name: Add Microsoft apt repository for MDATP
    apt_repository:
      repo: deb [arch=arm64,armhf,amd64] https://packages.microsoft.com/[distro]/[version]/prod [codename] main
      update_cache: yes
      state: present
      filename: microsoft-[channel]
    when: ansible_os_family == "Debian"

  - name: Add Microsoft DNF/YUM key
    rpm_key:
      state: present
      key: https://packages.microsoft.com/keys/microsoft.asc
    when: ansible_os_family == "RedHat"

  - name: Add  Microsoft yum repository for MDATP
    yum_repository:
      name: packages-microsoft-[channel]
      description: Microsoft Defender for Endpoint
      file: microsoft-[channel]
      baseurl: https://packages.microsoft.com/[distro]/[version]/[channel]/ 
      gpgcheck: yes
      enabled: Yes
    when: ansible_os_family == "RedHat"
  ```

- Ansible yüklemesi ve YAML dosyalarını oluşturun.

    - Apt tabanlı dağıtımlarda aşağıdaki YAML dosyasını kullanın:

        ```bash
        cat install_mdatp.yml
        ```
        ```Output
        - hosts: servers
          tasks:
            - include: ../roles/onboarding_setup.yml
            - include: ../roles/add_apt_repo.yml
            - name: Install MDATP
              apt:
                name: mdatp
                state: latest
                update_cache: yes
        ```

        ```bash
        cat uninstall_mdatp.yml
        ```
        ```Output
        - hosts: servers
          tasks:
            - name: Uninstall MDATP
              apt:
                name: mdatp
                state: absent
        ```

    - snf tabanlı dağıtımlarda aşağıdaki YAML dosyasını kullanın:

        ```bash
        cat install_mdatp_dnf.yml
        ```
        ```Output
        - hosts: servers
          tasks:
            - include: ../roles/onboarding_setup.yml
            - include: ../roles/add_yum_repo.yml
            - name: Install MDATP
              dnf:
                name: mdatp
                state: latest
                enablerepo: packages-microsoft-[channel]
        ```

        ```bash
        cat uninstall_mdatp_dnf.yml
        ```
        ```Output
        - hosts: servers
          tasks:
            - name: Uninstall MDATP
              dnf:
                name: mdatp
                state: absent
        ```

## <a name="deployment"></a>Dağıtım

Şimdi, görev dosyalarını ilgili dizin altında `/etc/ansible/playbooks/` veya ilgili dizinde çalıştırın.

- Yükleme:

    ```bash
    ansible-playbook /etc/ansible/playbooks/install_mdatp.yml -i /etc/ansible/hosts
    ```

> [!IMPORTANT]
> Ürün ilk kez başlatıldığında, en son kötü amaçlı yazılımdan koruma tanımlarını indirir. İnternet bağlantınıza bağlı olarak, bu birkaç dakika kadar sürebilir.

- Doğrulama/yapılandırma:

    ```bash
    ansible -m shell -a 'mdatp connectivity test' all
    ```
    ```bash
    ansible -m shell -a 'mdatp health' all
    ```

- Kaldırma:

    ```bash
    ansible-playbook /etc/ansible/playbooks/uninstall_mdatp.yml -i /etc/ansible/hosts
    ```

## <a name="log-installation-issues"></a>Günlük yükleme sorunları

Hata [oluştuğunda](linux-resources.md#log-installation-issues) yükleyici tarafından oluşturulan otomatik günlüğü bulma hakkında daha fazla bilgi için bkz. Günlük yükleme sorunları.

## <a name="operating-system-upgrades"></a>İşletim sistemi yükseltmeleri

İşletim sisteminizi yeni bir ana sürüme yükseltirken, önce Linux'ta Uç Nokta için Defender'ı kaldırmanız, yükseltmeyi yüklemeniz ve son olarak da cihazınıza Linux'ta Uç Nokta için Defender'ı yeniden yapılandırmanız gerekir.

## <a name="references"></a>Başvurular

- [BU DEPOLAMA birimlerini ekleme veya kaldırma](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/yum_repository_module.html)

- [Paket yöneticisiyle paketleri yönetme](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/dnf_module.html)

- [APT depolarını ekleme ve kaldırma](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_repository_module.html)

- [Apt-packages yönetme](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_module.html)

## <a name="see-also"></a>Ayrıca bkz.
- [Aracı durumu sorunlarını araştırma](health-status.md)
