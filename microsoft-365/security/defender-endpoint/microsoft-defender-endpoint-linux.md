---
title: Linux'ta Uç Nokta için Microsoft Defender
ms.reviewer: ''
description: Linux'ta Uç Nokta için Microsoft Defender yükleme ve kullanma işlemleri açıklanır.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, linux, installation, deploy, uninstallation, puppet, ansible, linux, redhat, ubuntu, debian, sles, suse, centos
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
ms.openlocfilehash: a5c6cd7b4fde3545f77cdece31f3693f74ca4444
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2022
ms.locfileid: "65669330"
---
# <a name="microsoft-defender-for-endpoint-on-linux"></a>Linux'ta Uç Nokta için Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Bu konuda Linux'ta Uç Nokta için Microsoft Defender yükleme, yapılandırma, güncelleştirme ve kullanma işlemleri açıklanmaktadır.

> [!CAUTION]
> Linux'ta Uç Nokta için Microsoft Defender birlikte diğer üçüncü taraf uç nokta koruma ürünlerini çalıştırmak, performans sorunlarına ve öngörülemeyen yan etkilere yol açabilir. Ortamınızda Microsoft dışı uç nokta koruması mutlak bir gereksinimse, virüsten koruma işlevini [Pasif modda](linux-preferences.md#enforcement-level-for-antivirus-engine) çalışacak şekilde yapılandırdıktan sonra Linux'ta Uç Nokta için Defender EDR işlevselliğinden güvenle yararlanabilirsiniz.

## <a name="how-to-install-microsoft-defender-for-endpoint-on-linux"></a>Linux'ta Uç Nokta için Microsoft Defender yükleme

Linux için Uç Nokta için Microsoft Defender kötü amaçlı yazılımdan koruma ve uç noktada algılama ve yanıtlama (EDR) özelliklerini içerir. 


### <a name="prerequisites"></a>Önkoşullar

- Microsoft 365 Defender portalına erişim
- [Sistemli](https://systemd.io/) sistem yöneticisini kullanarak Linux dağıtımı

  >[!NOTE]
  >RHEL/CentOS 6.x dışında sistem yöneticisi kullanan Linux dağıtımı hem SystemV hem de Upstart'ı destekler.

- Linux ve BASH betiği oluşturmada başlangıç düzeyinde deneyim
- Cihazdaki yönetim ayrıcalıkları (el ile dağıtım durumunda)

> [!NOTE]
> Linux aracısının Uç Nokta için Microsoft Defender [OMS aracısından](/azure/azure-monitor/agents/agents-overview#log-analytics-agent) bağımsızdır. Uç Nokta için Microsoft Defender kendi bağımsız telemetri işlem hattına dayanır.


### <a name="installation-instructions"></a>Yükleme yönergeleri

Linux'ta Uç Nokta için Microsoft Defender yüklemek ve yapılandırmak için kullanabileceğiniz çeşitli yöntemler ve dağıtım araçları vardır.

Genel olarak aşağıdaki adımları uygulamanız gerekir:

- Uç Nokta için Microsoft Defender aboneliğiniz olduğundan emin olun.
- Aşağıdaki dağıtım yöntemlerinden birini kullanarak Linux'ta Uç Nokta için Microsoft Defender dağıtın:
  - Komut satırı aracı:
    - [El ile dağıtım](linux-install-manually.md)
  - Üçüncü taraf yönetim araçları:
    - [Puppet yapılandırma yönetim aracını kullanarak dağıtma](linux-install-with-puppet.md)
    - [Ansible yapılandırma yönetim aracını kullanarak dağıtma](linux-install-with-ansible.md)
    - [Chef yapılandırma yönetim aracını kullanarak dağıtma](linux-deploy-defender-for-endpoint-with-chef.md)

Herhangi bir yükleme hatasıyla karşılaşırsanız [Bkz. Linux'ta Uç Nokta için Microsoft Defender yükleme hatalarını giderme](linux-support-install.md).

> [!NOTE]
> Uç Nokta için Microsoft Defender varsayılan yükleme yolu dışında başka bir konuma yüklenmesi desteklenmez. 

### <a name="system-requirements"></a>Sistem gereksinimleri

- Desteklenen Linux sunucu dağıtımları ve x64 (AMD64/EM64T) ve x86_64 sürümleri:

  - Red Hat Enterprise Linux 6.7 veya üzeri
  - Red Hat Enterprise Linux 7.2 veya üzeri
  - Red Hat Enterprise Linux 8.x
  - CentOS 6.7 veya üzeri 
  - CentOS 7.2 veya üzeri
  - Ubuntu 16.04 LTS veya üzeri LTS
  - Debian 9 veya üzeri
  - SUSE Linux Enterprise Server 12 veya üzeri
  - Oracle Linux 7.2 veya üzeri
  - Oracle Linux 8.x
  - Amazon Linux 2
  - Fedora 33 veya üzeri

    > [!NOTE]
    > Açıkça listelenmeyen dağıtımlar ve sürümler desteklenmez (resmi olarak desteklenen dağıtımlardan türetilmiş olsalar bile).

- Desteklenen çekirdek sürümlerinin listesi
  - En düşük çekirdek sürümü 3.10.0-327 (Red Hat Enterprise Linux 6 ve CentOS 6 dışında yukarıda belirtilen tüm desteklenen Linux dağıtımları için)
  - Çekirdek `fanotify` seçeneği etkinleştirilmelidir
  - Red Hat Enterprise Linux 6 ve CentOS 6:
    - 6.7 için: 2.6.32-573.*
    - 6.8 için: 2.6.32-642.*
    - 6.9 için: 2.6.32-696.* (2.6.32-696.el6.x86_64 hariç)
    - 6.10 için: 2.6.32-754.43.1 2.6.32.754.2.1.el6.x86_64:
    
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
       - 2.6.32-754.43.1.el6.x86_64
       - 2.6.32-754.47.1.el6.x86_64
       - 2.6.32-754.6.3.el6.x86_64
       - 2.6.32-754.9.1.el6.x86_64

 > [!NOTE]
 > Yeni bir paket sürümü yayımlandıktan sonra, önceki iki sürüme yönelik destek yalnızca teknik desteğe indirgener. Bu bölümde listelenen sürümlerden eski sürümler yalnızca teknik yükseltme desteği için sağlanır.


  > [!CAUTION]
  > Linux'ta Uç Nokta için Defender'ın diğer `fanotify`tabanlı güvenlik çözümleriyle yan yana çalıştırılması desteklenmez. İşletim sistemini asmak da dahil olmak üzere öngörülemeyen sonuçlara yol açabilir.

- Disk alanı: 1 GB

- /opt/microsoft/mdatp/sbin/wdavdaemon yürütülebilir izin gerektirir. Daha fazla bilgi için [Linux'ta Uç Nokta için Microsoft Defender yükleme sorunlarını giderme](/microsoft-365/security/defender-endpoint/linux-support-install) makalesindeki "Daemon'un yürütülebilir izinlere sahip olduğundan emin olun" konusuna bakın.

- Çekirdekler: 2 en az, 4 tercih edilir

- Bellek: En az 1 GB, tercih edilen 4 GB

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

Hizmeti etkinleştirdikten sonra, ağınızı veya güvenlik duvarınızı, bu hizmetle uç noktalarınız arasında giden bağlantılara izin verecek şekilde yapılandırmanız gerekebilir.

- Denetim çerçevesi (`auditd`) etkinleştirilmelidir.

  > [!NOTE]
  > 'a `/etc/audit/rules.d/` eklenen kurallar tarafından yakalanan sistem olayları ,'lere `audit.log`eklenir ve konak denetimini ve yukarı akış koleksiyonunu etkileyebilir. Linux'ta Uç Nokta için Microsoft Defender tarafından eklenen olaylar anahtarla `mdatp` etiketlenir.

### <a name="configuring-exclusions"></a>Dışlamaları Yapılandırma

Microsoft Defender Virüsten Koruma'a dışlama eklerken, Microsoft Defender Virüsten Koruma [için Yaygın Dışlama Hatalarına](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus) dikkat etmelisiniz

### <a name="network-connections"></a>Ağ bağlantıları

Aşağıdaki indirilebilir elektronik tablo, ağınızın bağlanabilmesi gereken hizmetleri ve bunların ilişkili URL'lerini listeler. Bu URL'lere erişimi reddedecek bir güvenlik duvarı veya ağ filtreleme kuralı olmadığından emin olmalısınız. Varsa, bunlar için özel olarak bir *izin verme* kuralı oluşturmanız gerekebilir.

<br>

****

|Etki alanları listesinin elektronik tablosu| Açıklama|
|---|---|
|Ticari müşteriler için Uç Nokta için Microsoft Defender URL listesi| Ticari müşteriler için hizmet konumları, coğrafi konumlar ve işletim sistemi için belirli DNS kayıtlarının elektronik tablosu. <p> [Elektronik tabloyu buradan indirin.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Gov/GCC/DoD için Uç Nokta için Microsoft Defender URL listesi | Gov/GCC/DoD müşterileri için hizmet konumları, coğrafi konumlar ve işletim sistemi için belirli DNS kayıtlarının elektronik tablosu. <p> [Elektronik tabloyu buradan indirin.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

> [!NOTE]
> Daha belirli bir URL listesi için bkz. [Ara sunucu ve internet bağlantısı ayarlarını yapılandırma](/microsoft-365/security/defender-endpoint/configure-proxy-internet#enable-access-to-microsoft-defender-atp-service-urls-in-the-proxy-server).

Uç Nokta için Defender, aşağıdaki bulma yöntemlerini kullanarak bir proxy sunucusu bulabilir:

- Saydam ara sunucu
- El ile statik proxy yapılandırması

Bir ara sunucu veya güvenlik duvarı anonim trafiği engelliyorsa, önceden listelenen URL'lerde anonim trafiğe izin verildiğinden emin olun. Saydam proxy'ler için Uç Nokta için Defender için ek yapılandırma gerekmez. Statik ara sunucu için [El ile Statik Proxy Yapılandırması'ndaki](linux-static-proxy-configuration.md) adımları izleyin.

> [!WARNING]
> PAC, WPAD ve kimliği doğrulanmış proxy'ler desteklenmez. Yalnızca statik bir ara sunucu veya saydam proxy kullanıldığından emin olun.
>
> GÜVENLIK nedeniyle SSL denetimi ve ara sunucuları da desteklenmez. SSL incelemesi için bir özel durum yapılandırın ve ara sunucunuzu, Linux'ta Uç Nokta için Defender'dan kesme olmadan ilgili URL'lere doğrudan veri geçirmek için yapılandırın. Kesme sertifikanızı genel depoya eklemek kesmeye izin vermez.

Sorun giderme adımları için bkz[. Linux'ta Uç Nokta için Microsoft Defender için bulut bağlantısı sorunlarını giderme](linux-support-connectivity.md).

## <a name="how-to-update-microsoft-defender-for-endpoint-on-linux"></a>Linux'ta Uç Nokta için Microsoft Defender güncelleştirme

Microsoft, performansı, güvenliği geliştirmek ve yeni özellikler sunmak için düzenli olarak yazılım güncelleştirmeleri yayımlar. Linux'ta Uç Nokta için Microsoft Defender güncelleştirmek için bkz. [Linux'ta Uç Nokta için Microsoft Defender güncelleştirmelerini dağıtma](linux-updates.md).

## <a name="how-to-configure-microsoft-defender-for-endpoint-on-linux"></a>Linux'ta Uç Nokta için Microsoft Defender yapılandırma

Ürünü kurumsal ortamlarda yapılandırma yönergelerine [Linux'ta Uç Nokta için Microsoft Defender için tercihleri ayarlama](linux-preferences.md) bölümünden ulaşabilirsiniz.

## <a name="common-applications-to-microsoft-defender-for-endpoint-can-impact"></a>Uç Nokta için Microsoft Defender için Yaygın Uygulamalar etkilenebilir

Belirli uygulamaların yüksek G/Ç iş yükleri, Uç Nokta için Microsoft Defender yüklendiğinde performans sorunlarıyla karşılaşabilir. Bunlar Jenkins ve Jira gibi geliştirici senaryolarına yönelik uygulamaları ve OracleDB ve Postgres gibi veritabanı iş yüklerini içerir. Performans düşüşü yaşıyorsanız, Microsoft Defender Virüsten Koruma için Yaygın Dışlama Hatalarını göz önünde bulundurarak güvenilen uygulamalar [için dışlamalar](/microsoft-365/security/defender-endpoint/common-exclusion-mistakes-microsoft-defender-antivirus) ayarlamayı göz önünde bulundurun. Ek yönergeler için üçüncü taraf uygulamalardan gelen virüsten koruma dışlamalarıyla ilgili danışmanlık belgelerini göz önünde bulundurun.

## <a name="resources"></a>Kaynaklar

- Günlüğe kaydetme, kaldırma veya diğer konular hakkında daha fazla bilgi için bkz [. Kaynaklar](linux-resources.md).
  
## <a name="related-articles"></a>İlgili makaleler
  
-  [uç noktalarınızı Bulut için Defender tümleşik EDR çözümüyle koruyun: Uç Nokta için Microsoft Defender](/azure/defender-for-cloud/integration-defender-for-endpoint)
-  [Azure dışı makinelerinizi Bulut için Microsoft Defender Bağlan](/azure/defender-for-cloud/quickstart-onboard-machines)

