---
title: Linux'ta Uç Nokta için Microsoft Defender'ın yükleme sorunlarını giderme
ms.reviewer: ''
description: Linux'ta Uç Nokta için Microsoft Defender'ın yükleme sorunlarını giderme
keywords: microsoft, defender, Endpoint için Microsoft Defender, linux, yükleme
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
ms.openlocfilehash: a0b2a571be5f78818279a343d253709e05814908
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011885"
---
# <a name="troubleshoot-installation-issues-for-microsoft-defender-for-endpoint-on-linux"></a>Linux'ta Uç Nokta için Microsoft Defender'ın yükleme sorunlarını giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

## <a name="verify-that-the-installation-succeeded"></a>Yüklemenin başarılı olduğunu doğrulama

Yükleme sırasında bir hata, paket yöneticisi tarafından anlamlı bir hata iletisine neden olabilir veya ortaya çıkan bir hata iletisiyle sonuçlanmayacaktır. Yüklemenin başarılı olup olduğunu doğrulamak için, şunları kullanarak yükleme günlüklerini alın ve kontrol edin:

```bash
 sudo journalctl --no-pager|grep 'microsoft-mdatp' > installation.log
```

```bash
 grep 'postinstall end' installation.log
```

```Output
 microsoft-mdatp-installer[102243]: postinstall end [2020-03-26 07:04:43OURCE +0000] 102216
```

Yüklemenin tarih ve saati doğru olan bir önceki komutun çıktısı başarılı olduğunu gösterir.

Ayrıca, [ürünün durumunu doğrulamak](linux-install-manually.md#client-configuration) ve EICAR metin dosyasını algılamak için İstemci yapılandırmasını kontrol edin.

## <a name="make-sure-you-have-the-correct-package"></a>Doğru pakete sahip olduğundan emin olun

Yüklemekte olan paketin ana bilgisayar dağıtımı ve sürümüyle eşleni olduğunu doğrulayın.

<br>

****

|paket|dağıtım|
|---|---|
|mdatp-rhel8. Linux.x86_64.rpm|Oracle, RHEL ve CentOS 8.x|
|mdatp-sles12. Linux.x86_64.rpm|SUSE Linux Enterprise Server 12.x|
|mdatp-sles15. Linux.x86_64.rpm|SUSE Linux Enterprise Server 15.x|
|mdatp. Linux.x86_64.rpm|Oracle, RHEL ve CentOS 7.x|
|mdatp. Linux.x86_64.deb|Debian ve Ubuntu 16.04, 18.04 ve 20.04|
|

El [ile dağıtım](linux-install-manually.md) için doğru dağıtımın ve sürümün seçilmiş olduğundan emin olun.

## <a name="installation-failed"></a>Yükleme başarısız oldu

Uç Nokta için Defender hizmetinin çalışıyor olup olduğunu kontrol edin:

```bash
service mdatp status
```

```Output
 ● mdatp.service - Microsoft Defender for Endpoint
   Loaded: loaded (/lib/systemd/system/mdatp.service; enabled; vendor preset: enabled)
   Active: active (running) since Thu 2020-03-26 10:37:30 IST; 23h ago
 Main PID: 1966 (wdavdaemon)
    Tasks: 105 (limit: 4915)
   CGroup: /system.slice/mdatp.service
           ├─1966 /opt/microsoft/mdatp/sbin/wdavdaemon
           ├─1967 /opt/microsoft/mdatp/sbin/wdavdaemon
           └─1968 /opt/microsoft/mdatp/sbin/wdavdaemon
 ```

## <a name="steps-to-troubleshoot-if-the-mdatp-service-isnt-running"></a>mdatp hizmeti çalışmıyorsa sorun giderme adımları

1. "mdatp" kullanıcı var olup olduğunu kontrol edin:

    ```bash
    id "mdatp"
    ```

    Çıktı yoksa

    ```bash
    sudo useradd --system --no-create-home --user-group --shell /usr/sbin/nologin mdatp
    ```

2. Aşağıdakini kullanarak hizmeti etkinleştirmeyi ve yeniden başlatmayı deneyin:

    ```bash
    sudo service mdatp start
    ```

    ```bash
    sudo service mdatp restart
    ```

3. Önceki komutu çalıştırmakta mdatp.service bulunamıyorsa, çalıştırın:

    ```bash
    sudo cp /opt/microsoft/mdatp/conf/mdatp.service <systemd_path> 
    ```

    Ubuntu `<systemd_path>` ve `/lib/systemd/system` Debian dağıtımları ve /usr/lib/systemd/system' için Rhel, CentOS, Oracle ve SLES için ise. Sonra 2. adımı yeniden çalıştır.

4. Yukarıdaki adımlar işe yaramadı mı, SELinux'in yüklü ve zorlanma modunda olup olmadığını kontrol edin. Öyleyse izinli (tercihen) veya devre dışı moduna ayarlamayı deneyin. Bu işlemi, dosyada "izin verilen `SELINUX` " veya "devre dışı" `/etc/selinux/config` olarak parametreyi yeniden başlatma işlemi başlatarak yapılabilir. Daha fazla bilgi için selinux'un man-page'ine bakın.
Şimdi 2. adımı kullanarak mdatp hizmetini yeniden başlatmayı deneyin. Güvenlik nedeniyle, bunu çalıştırıp yeniden başlattıktan sonra yapılandırma değişikliğini hemen geri döndürin.

5. Dizin `/opt` sembolik bir bağlantı ise, için bir bağlama bağlaması oluşturun `/opt/microsoft`.

6. Daemon'un yürütülebilir izni olduğundan emin olun.

    ```bash
    ls -l /opt/microsoft/mdatp/sbin/wdavdaemon
    ```

    ```Output
    -rwxr-xr-x 2 root root 15502160 Mar  3 04:47 /opt/microsoft/mdatp/sbin/wdavdaemon
    ```

    Daemon'un yürütülebilir izinleri yoksa, aşağıdakini kullanarak yürütülebilir dosyası dosyası olun:

    ```bash
    sudo chmod 0755 /opt/microsoft/mdatp/sbin/wdavdaemon
    ```

    ve 2. adımı çalıştırmayı yeniden deneyin.

7. wdavdaemon içeren dosya sisteminin "noexec" ile bağlı olmadığını kontrol etme.

## <a name="if-the-defender-for-endpoint-service-is-running-but-the-eicar-text-file-detection-doesnt-work"></a>Uç nokta için Defender hizmeti çalışıyor, ancak EICAR metin dosyası algılaması çalışmıyorsa

1. Aşağıdakini kullanarak dosya sistem türünü kontrol edin:

    ```bash
    findmnt -T <path_of_EICAR_file>
    ```

    Şu anda erişime uygun etkinlikler için desteklenen dosya sistemleri burada [listelenmiştir](microsoft-defender-endpoint-linux.md#system-requirements). Bu dosya sistemlerinin dışındaki dosyalar taranmaz.

## <a name="command-line-tool-mdatp-isnt-working"></a>"mdatp" komut satırı aracı çalışmıyor

1. Komut satırı aracını çalıştırmak hata `mdatp` veriyorsa `command not found`, aşağıdaki komutu çalıştırın:

    ```bash
    sudo ln -sf /opt/microsoft/mdatp/sbin/wdavdaemonclient /usr/bin/mdatp
    ```

    ve yeniden deneyin.

    Yukarıdaki adımlardan hiçbiri yardımcı olmazsa, tanılama günlüklerini toplayın:

    ```bash
    sudo mdatp diagnostic create
    ```

    ```Output
    Diagnostic file created: <path to file>
    ```

    Günlükleri içeren bir zip dosyasının yolu çıktı olarak görüntülenir. Bu günlüklerle müşteri desteğimize başvurun.
