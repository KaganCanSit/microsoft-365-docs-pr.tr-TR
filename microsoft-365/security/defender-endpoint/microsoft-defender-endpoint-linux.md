---
title: Linux'ta Uç Nokta için Microsoft Defender
ms.reviewer: ''
description: Linux'ta Uç Nokta için Microsoft Defender'ı yükleme ve kullanma açıklarıdır.
keywords: microsoft, defender, Endpoint için Microsoft Defender, linux, yükleme, dağıtma, kaldırma, ssible, linux, redhat, ubuntu, debian, sles, suse, centos
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
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: ebc5c0bfad32da316368c5c440fed23df28e9e17
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011850"
---
# <a name="microsoft-defender-for-endpoint-on-linux"></a>Linux'ta Uç Nokta için Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Bu konuda, Linux'ta Uç Nokta için Microsoft Defender'ı yükleme, yapılandırma, güncelleştirme ve kullanma açıklanmıştır.

> [!CAUTION]
> Linux'ta Uç Nokta için Microsoft Defender ile birlikte diğer üçüncü taraf uç nokta koruma ürünlerinin de çalıştır olması performans sorunlarına ve öngörülemeyen yan etkilere neden olabilir. Microsoft dışı uç nokta koruması ortamınızın mutlak bir gereksinimi ise, virüsten koruma işlevini Pasif modunda çalıştıracak şekilde yapılandırdikten sonra Linux EDR uç noktası için Defender'ın avantajını güvenle [kullanabilirsiniz](linux-preferences.md#enforcement-level-for-antivirus-engine).

## <a name="how-to-install-microsoft-defender-for-endpoint-on-linux"></a>Linux'ta Uç Nokta için Microsoft Defender'ı yükleme

### <a name="prerequisites"></a>Önkoşullar

- Microsoft 365 Defender portalına erişim
- Sistemli sistem [yöneticisini kullanarak](https://systemd.io/) Linux dağıtımı
- Linux ve BASH betikleri için başlangıç düzeyi deneyimi
- Cihaz üzerinde yönetim ayrıcalıkları (el ile dağıtım durumunda)

> [!NOTE]
> Linux'ta Uç Nokta için Microsoft Defender aracısı [OMS aracılarından bağımsızdır](/azure/azure-monitor/agents/agents-overview#log-analytics-agent). Uç Nokta için Microsoft Defender kendi bağımsız telemetri potansiyel sistemine dayanıyor.


### <a name="installation-instructions"></a>Yükleme yönergeleri

Linux'ta Uç Nokta için Microsoft Defender'ı yüklemek ve yapılandırmak için kullanabileceğiniz çeşitli yöntemler ve dağıtım araçları vardır.

Genelde aşağıdaki adımları benimsersiniz:

- Uç nokta için Microsoft Defender aboneliğiniz olduğundan emin olun.
- Aşağıdaki dağıtım yöntemlerinden birini kullanarak Linux'ta Uç Nokta için Microsoft Defender'ı dağıtın:
  - Komut satırı aracı:
    - [El ile dağıtım](linux-install-manually.md)
  - Üçüncü taraf yönetim araçları:
    - [Configuration configuration management tool kullanarak dağıtma](linux-install-with-puppet.md)
    - [Ansible yapılandırma yönetim aracını kullanarak dağıtma](linux-install-with-ansible.md)
    - [Configuration yapılandırma yönetim aracını kullanarak dağıtma](linux-deploy-defender-for-endpoint-with-chef.md)

Yükleme hatalarına sahipseniz Linux'ta Uç Nokta [için Microsoft Defender'da yükleme sorunlarını giderme'ye bakın](linux-support-install.md).

> [!NOTE]
> Varsayılan yükleme yolu dışında herhangi bir konumda Uç Nokta için Microsoft Defender'ın yüklü olması desteklenmiyor. 

### <a name="system-requirements"></a>Sistem gereksinimleri

- Desteklenen Linux sunucu dağıtımları ve x64 (AMD64/EM64T) sürümleri:

  - Red Hat Enterprise Linux 6.7 veya daha yüksek
  - Red Hat Enterprise Linux 7.2 veya daha yüksek
  - Red Hat Enterprise Linux 8.x
  - CentOS 6.7 veya daha yüksek 
  - CentOS 7.2 veya daha yüksek
  - Ubuntu 16.04 LTS veya daha yüksek LTS
  - Debian 9 veya daha yüksek
  - SUSE Linux Enterprise Server 12 veya daha yüksek sürümü
  - Oracle Linux 7.2 veya daha yüksek
  - Amazon Linux 2
  - Fedora 33 veya daha yüksek

    > [!NOTE]
    > Açıkça listelenmiyor dağıtımlar ve sürümler desteklenmiyor (resmi olarak desteklenen dağıtımlardan türetlenmiş olsalar bile).

- Desteklenen çekirdek sürümlerinin listesi
  - Red Hat Enterprise Linux 6 ve CentOS 6:
    - 6.7 için: 2.6.32-573.*
    - 6.8 için: 2.6.32-642.*
    - 6.9 için: 2.6.32-696.*
    - 6.10 için: 2.6.32.754.2.1.el6.x86_64 2.6.32-754.41.2'ye 2.6.32.754.2.1.el6.x86_64:
    
       - 2.6.32-754.10.1.el6.x86_64
       - 2.6.32-754.11.1.el6.x86_64
       - 2.6.32-754.12.1.el6.x86_64
       - 2.6.32-754.14.2.el6.x86_64
       - 2.6.32-754.15.3.el6.x86_64
       - 2.6.32-754.17.1.el6.x86_64
       - 2.6.32-754.18.2.el6.x86_64
       - 2.6.32-754.2.1.el6.x86_64
       - 2.6.32-754.22.1.el6.x86_64
       - 2.6.32-754.23.1.el6.x86_64
       - 2.6.32-754.24.2.el6.x86_64
       - 2.6.32-754.24.3.el6.x86_64
       - 2.6.32-754.25.1.el6.x86_64
       - 2.6.32-754.27.1.el6.x86_64
       - 2.6.32-754.28.1.el6.x86_64
       - 2.6.32-754.29.1.el6.x86_64
       - 2.6.32-754.29.2.el6.x86_64
       - 2.6.32-754.3.5.el6.x86_64
       - 2.6.32-754.30.2.el6.x86_64
       - 2.6.32-754.33.1.el6.x86_64
       - 2.6.32-754.35.1.el6.x86_64
       - 2.6.32-754.39.1.el6.x86_64
       - 2.6.32-754.41.2.el6.x86_64
       - 2.6.32-754.6.3.el6.x86_64
       - 2.6.32-754.9.1.el6.x86_64


    > [!NOTE]
    > Yeni bir paket sürümü yayınlandıktan sonra, önceki iki sürümün desteği yalnızca teknik destekle azaltıldı. Bu bölümde listelenenden daha eski sürümler yalnızca teknik yükseltme desteği için sağlanmıştır.

  - Desteklenen dağıtımların geri kalanı için, gereken en düşük çekirdek sürümü 3.10.0-327'dir

- Olay sağlayıcısı mekanizması
  - Red Hat Enterprise Linux 6 ve CentOS 6: `Talpa` Çekirdek modülü tabanlı çözüm
  - Desteklenen diğer dağıtımlar için: `Fanotify`
    - Çekirdek `fanotify` seçeneğinin etkinleştirilmesi gerekir

      > [!CAUTION]
      > Linux'ta Uç Nokta için diğer tabanlı güvenlik `fanotify`çözümleriyle yan yana çalışan Defender desteklenmiyor. İşletim sisteminin asılı olması da dahil olmak üzere, öngörülemeyen sonuçlara yol aç sağlar.

- Disk alanı: 1 GB

- /opt/microsoft/mdatp/sbin/wdavdaemon için yürütülebilir izin gerekir. Daha fazla bilgi için Linux'ta Uç Nokta için Microsoft Defender yükleme sorunlarını giderme makalesinde "daemon'da yürütülebilir izin olduğundan emin olun" [makalesine bakın](/microsoft-365/security/defender-endpoint/linux-support-install).

- Çekirdekler: En az 2, 4 tercih edilen

- Bellek: En az 1 GB, tercih edilen 4

    > [!NOTE]
    > Lütfen /var içinde boş disk alanınız olduğundan emin olun.

- Çözüm şu anda aşağıdaki dosya sistemi türleri için gerçek zamanlı koruma sağlar:

  - `btrfs`
  - `ecryptfs`
  - `ext2`
  - `ext3`
  - `ext4`
  - `fuse`
  - `fuseblk`
  - `jfs`
  - `nfs`
  - `overlay`
  - `ramfs`
  - `reiserfs`
  - `tmpfs`
  - `udf`
  - `vfat`
  - `xfs`

Hizmeti etkinleştirdikten sonra, ağ veya güvenlik duvarınızı bu bağlantıyla uç noktalarınız arasında giden bağlantılara izin verecek şekilde yapılandırmanız gerekebilir.

- Denetim çerçevesi (`auditd`) etkinleştirilmelidir.

  > [!NOTE]
  > Kuralların eklediği sistem olayları `/etc/audit/rules.d/` `audit.log`(s) değerine eklenir ve ana bilgisayar denetimini ve akış koleksiyonunu etkileyebilir. Linux'ta Uç Nokta için Microsoft Defender tarafından eklenen olaylar anahtarla etiketlenir `mdatp` .

### <a name="configuring-exclusions"></a>Dışlamaları Yapılandırma

Dışlamalar söz Microsoft Defender Virüsten Koruma, hatanın Yaygın Dışlama [Hatalarını Microsoft Defender Virüsten Koruma](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus)

### <a name="network-connections"></a>Ağ bağlantıları

Aşağıdaki indirilebilir elektronik tablo, ağ bağlantı kurabilirsiniz ve bu hizmetlerle ilişkilendirilmiş URL'leri listeler. Bu URL'lere erişimi reddedecek güvenlik duvarı veya ağ filtreleme kuralları yoktur. Varsa, özel olarak onlar için bir izin *kuralı* oluşturmanız gerekir.

<br>

****


|Etki alanı listesinin elektronik tablosu| Açıklama|
|---|---|
|Ticari müşteriler için Uç Nokta URL listesi için Microsoft Defender | Ticari müşteriler için hizmet konumları, coğrafi konumlar ve işletim sistemi için belirli DNS kayıtlarının elektronik tablosu. <p> [Elektronik tabloyu buradan indirin.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Gov/GCC/DoD müşterileri için Uç nokta URL listesi için Microsoft Defender| Gov/GCC/DoD müşterileri için hizmet konumları, coğrafi konumlar ve işletim sistemi için belirli DNS kayıtlarının elektronik tablosu. <p> [Elektronik tabloyu buradan indirin.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)
|


> [!NOTE]
> Daha belirli bir URL listesi için bkz. [Proxy ve İnternet bağlantı ayarlarını yapılandırma](/microsoft-365/security/defender-endpoint/configure-proxy-internet#enable-access-to-microsoft-defender-atp-service-urls-in-the-proxy-server).

Uç Nokta için Defender, aşağıdaki bulma yöntemlerini kullanarak bir ara sunucuyu keşfeder:

- Saydam ara sunucu
- El ile statik ara sunucu yapılandırması

Bir ara sunucu veya güvenlik duvarı anonim trafiği engelliyorsa, anonim trafiğin daha önce listelenen URL'lerde izin verildiğindan emin olun. Saydamxlarda, Uç Nokta için Defender'a ek yapılandırma gerekmez. Statik proxy için, El ile Statik Proxy [Yapılandırması'nın adımlarını izleyin](linux-static-proxy-configuration.md).

> [!WARNING]
> PAC, WPAD ve kimliği doğrulanmışxler desteklanmaz. Yalnızca statik ara sunucu veya saydam proxy'nin kullanılıyor olduğundan emin olun.
>
> SSL incelemesi ve kesişme prox'leri güvenlik nedenleriyle de desteklanmaz. Linux'ta Uç Nokta için Defender'dan kesme noktası olmadan ilgili URL'lere doğrudan veri geçecek SSL incelemesi ve ara sunucu için bir özel durum yapılandırın. Kesme noktası sertifikanızı genel mağazaya eklemek kesme noktası engellemesine izin vermez.

Sorun giderme adımları için bkz [. Linux'ta Uç Nokta için Microsoft Defender'da bulut bağlantısı sorunlarını giderme](linux-support-connectivity.md).

## <a name="how-to-update-microsoft-defender-for-endpoint-on-linux"></a>Linux'ta Uç Nokta için Microsoft Defender'ı güncelleştirme

Microsoft, performansı, güvenliği geliştirmek ve yeni özellikler sunmak için düzenli olarak yazılım güncelleştirmeleri yayımlar. Linux'ta Uç Nokta için Microsoft Defender'ı güncelleştirmek için Linux'ta [Uç Nokta için Microsoft Defender güncelleştirmelerini dağıtma'ya bakın](linux-updates.md).

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-linux"></a>Linux'ta Uç Nokta için Microsoft Defender nasıl yapılandırılır

Ürünü kurumsal ortamlarda yapılandırma kılavuzuna Linux'ta Uç nokta için [Microsoft Defender tercihlerini ayarlama makalesinde bulunmaktadır](linux-preferences.md).

## <a name="common-applications-to-microsoft-defender-for-endpoint-can-impact"></a>Uç Nokta için Microsoft Defender'ın Yaygın Uygulamaları etkileyebilirsiniz

Uç Nokta için Microsoft Defender yüklü olduğunda, bazı uygulamalardan gelen yüksek I/O iş yükleri performans sorunlarıyla neden olabilir. Bunlar, Oracle ve Jira gibi geliştirici senaryoları için uygulamalar, OracleDB ve Postgres gibi veritabanı iş yükleridir. Performans düşüşü yaşıyorsanız, güvenilir uygulamalar için dışlamalar ayarlamayı göz önünde bulundurarak Dışlama Hatalarının Yaygın [Microsoft Defender Virüsten Koruma](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus) göz önünde bulundurabilirsiniz. Ek bilgiler için, üçüncü taraf uygulamalardan virüsten koruma dışlamaları ile ilgili belgelere bakabilirsiniz.

## <a name="resources"></a>Kaynaklar

- Günlüğe kaydetme, kaldırma veya diğer konular hakkında daha fazla bilgi için bkz. [Kaynaklar](linux-resources.md).
