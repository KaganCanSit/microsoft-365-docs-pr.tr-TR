---
title: Linux RHEL6'da Uç Nokta için Microsoft Defender sorunlarını giderme
ms.reviewer: ''
description: Linux'ta Uç Nokta için Microsoft Defender'da bulut bağlantı sorunlarını giderme
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, linux, bulut, bağlantı, iletişim
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 43a60d12883dc639c4ee5b831d305010cef58533
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998026"
---
# <a name="troubleshoot-issues-for-microsoft-defender-for-endpoint-on-linux-rhel6"></a>Linux RHEL6'da Uç Nokta için Microsoft Defender sorunlarını giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Bu makale, Red Hat Linux 6 (RHEL 6) veya daha yeni bir sürümü üzerinde Linux için Microsoft Defender ile karşılaşabilirsiniz sorunları giderme konusunda yol gösterici bilgi sağlar. 

Paket (mdatp_XXX.XX.XX.XX.x86_64.rpm) yüklendikten sonra, yüklemenin başarılı olduğunu doğrulamak için gereken işlemleri gerçekleştirin. 


## <a name="check-the-service-health"></a>Hizmet durumunu denetleme

Hizmet durumunu kontrol etmek için aşağıdaki komutu kullanın:

```bash
mdatp health 
```

## <a name="verify-that-the-service-is-running"></a>Hizmetin çalıştığını doğrulama

Hizmetin çalıştığını doğrulamak için aşağıdaki komutu kullanın:

```bash
service mdatp status 
```

Beklenen çıkış: `mdatp start/running, process 4517`

## <a name="verify-the-distribution-and-kernel-version"></a>Dağılımı ve çekirdek sürümünü doğrulama
Dağılımın ve çekirdek sürümlerinin desteklenenler listesinde olması gerekir.

Dağıtım sürümünü almak için aşağıdaki komutu kullanın:

```bash
cat /etc/redhat-release (or /etc/system-release) 
```

Çekirdek sürümünü almak için aşağıdaki komutu kullanın:

```bash
uname -r
```
## <a name="check-if-mdatp-audisp-process-is-running"></a>mdatp audisp işleminin çalıştır olup olduğunu denetleme 
Beklenen çıkış, sürecin çalışıyor olmasıdır.

Şunları kontrol etmek için aşağıdaki komutu kullanın:

```bash
pidof mdatp_audisp_plugin 
```

## <a name="check-talpa-modules"></a>TALPA modüllerini denetleme
Yüklenmiş dokuz modül olması gerekir. 

Şunları kontrol etmek için aşağıdaki komutu kullanın:

```bash
lsmod | grep talpa
```

Beklenen çıkış: Etkin

```bash
talpa_pedconnector       878  0 

talpa_pedevice          5189  2 talpa_pedconnector 

talpa_vfshook          32300  1 

talpa_vcdevice          4947  1 

talpa_syscall           9127  0 

talpa_core             90699  4 talpa_vfshook,talpa_vcdevice,talpa_syscall 

talpa_linux            29424  5 talpa_vfshook,talpa_vcdevice,talpa_syscall,talpa_core 

talpa_syscallhookprobe      882  0 

talpa_syscallhook      14987  2 talpa_vfshook,talpa_syscallhookprobe 
```


```bash
lsmod | grep talpa | wc -l 
```

Beklenen çıkış: 9

## <a name="check-talpa-status"></a>TALPA durumunu denetleme

```bash
cat /proc/sys/talpa/interceptors/VFSHookInterceptor/status 
```

Günlük dosyalarını ayıklama ('mdatp tanılama oluşturma' paketi dışında) 

```bash
/var/log/audit/audit.log 

/var/log/messages 

semanage fcontext -l > selinux.log 
```
 

Performans ve Bellek 

```bash
top -p <wdavdaemon pid>      

pmap -x <wdavdaemon pid> 
```

kullanarak `<wdavdaemon pid>` nerede bulunabilir?`pidof wdavdaemon`

