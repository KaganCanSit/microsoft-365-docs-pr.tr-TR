---
title: Uç nokta (Linux) için Microsoft Defender güncelleştirmesini zamanlama
description: Kuruluş varlıklarını daha iyi korumak için Uç Nokta (Linux) için Microsoft Defender güncelleştirmesini zamanlamayı öğrenin.
keywords: microsoft, defender, Endpoint için Microsoft Defender, linux, taramalar, virüsten koruma, uç nokta için Microsoft Defender (linux)
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 6fb3141b33948c5c452096c83a2f02657c199575
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2022
ms.locfileid: "63450556"
---
# <a name="schedule-an-update-of-the-microsoft-defender-for-endpoint-linux"></a>Uç Nokta (Linux) için Microsoft Defender güncelleştirmesini zamanlama

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Linux'ta Uç Nokta için Microsoft Defender'da bir güncelleştirme çalıştırmak için bkz. [Linux'ta Uç Nokta için Microsoft Defender güncelleştirmelerini dağıtma](/microsoft-365/security/defender-endpoint/linux-updates).

Linux (ve Unix), zamanlanmış görevleri çalıştırabilecek **crontab** (Görev Zamanlayıcı gibi) adlı bir araciya sahip.

## <a name="pre-requisite"></a>Önkul

> [!NOTE]
> Tüm saat dilimlerinin listesini almak için aşağıdaki komutu çalıştırın: `timedatectl list-timezones`
>
> Saat dilimleri için örnekler:
>
> - `America/Los_Angeles`
> - `America/New_York`
> - `America/Chicago`
> - `America/Denver`

## <a name="to-set-the-cron-job"></a>Cron işini ayarlamak için

Aşağıdaki komutları kullanın:

### <a name="backup-crontab-entries"></a>Çapraz girdileri yedekleme

```bash
sudo crontab -l > /var/tmp/cron_backup_201118.dat
```

> [!NOTE]
> Burada 201118 == YYAAAA

> [!TIP]
> Düzenlemeden veya kaldırmadan önce bunu yapmak.

Kırpmayı düzenlemek ve kök kullanıcı olarak yeni bir iş eklemek için:

```bash
sudo crontab -e
```

> [!NOTE]
> Varsayılan düzenleyici VIM'dir.

Şunları da görüyor olabileceğiniz gibi:

```output
0****/etc/opt/microsoft/mdatp/logrorate.sh
```

Ve

```output
02**sat /bin/mdatp scan quick>~/mdatp_cron_job.log
```

Bkz [. Uç Nokta (Linux) için Microsoft Defender ile tarama zamanlama](linux-schedule-scan-mde.md)

"Ekle" tuşuna basın

Aşağıdaki girdileri ekleyin:

```bash
CRON_TZ=America/Los_Angeles
```

> #<a name="rhel-and-variants-centos-and-oracle-linux"></a>! RHEL ve çeşitlemeler (CentOS ve Oracle Linux)
>
> ```bash
> 0 6 * * sun [ $(date +%d) -le 15 ] && sudo yum update mdatp -y >> ~/mdatp_cron_job.log
> ```

> #<a name="sles-and-variants"></a>! SLES ve çeşitlemeler
>
> ```bash
> 0 6 * * sun [ $(date +%d) -le 15 ] && sudo zypper update mdatp >> ~/mdatp_cron_job.log
> ```

> #<a name="ubuntu-and-debian-systems"></a>! Ubuntu ve Debian sistemleri
>
> ```bash
> 0 6 * * sun [ $(date +%d) -le 15 ] && sudo apt-get install --only-upgrade mdatp >> ~/mdatp_cron_job.log
> ```

> [!NOTE]
> Yukarıdaki örneklerde, bunu Pazar günleri 00 dakika, 6 saat (24 saat biçiminde saat), ayın herhangi bir günü, herhangi bir ayın herhangi bir günü olarak ayarlarız. [$(date +\%d) -le 15] == 15. gün (3. hafta) eşit veya daha küçük olmadıkça çalışmaz. Yani, ayın 3'üncü Pazarlarında(7) sabah 6:00'da çalıştırılacaktır. Pasifik (UTC -8).

"Esc" tuşuna basın

Çift tırnak içine "`:wq`" yazın.

> [!NOTE]
> w == write, q == quit

İşlerinizi görüntülemek için `sudo crontab -l`

:::image type="content" source="images/update-MDE-linux-4634577.jpg" alt-text="Linux'ta Uç Nokta için Defender Güncelleştirmesi.":::

İş ilanlarını incelemek için:

```bash
sudo grep mdatp /var/log/cron
```

mdatp_cron_job.log dosyasını incelemek için

```bash
sudo nano mdatp_cron_job.log
```

## <a name="for-those-who-use-ansible-chef-or-puppet"></a>Ansible,Sina veya Yalçın'i kullananlar için

Aşağıdaki komutları kullanın:

### <a name="to-set-cron-jobs-in-ansible"></a>Ansible'da iş kırpmayı ayarlamak için

```bash
cron - Manage cron.d and crontab entries
```

Daha <https://docs.ansible.com/ansible/latest/modules/cron_module.html> fazla bilgi için bkz.

### <a name="to-set-crontabs-in-chef"></a>Crontabs in Veya Veya irdele'i ayarlamak için

```bash
cron resource
```

Daha <https://docs.chef.io/resources/cron/> fazla bilgi için bkz.

### <a name="to-set-cron-jobs-in-puppet"></a>Jobs'ta iş kırpmayı ayarlamak için

Kaynak Türü: cron

Daha <https://puppet.com/docs/puppet/5.5/types/cron.html> fazla bilgi için bkz.

Çiğdem: Cron işleri ve zamanlanmış görevlerle otomatik oluşturma

Daha <https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/> fazla bilgi için bkz.

## <a name="additional-information"></a>Ek bilgiler

### <a name="to-get-help-with-crontab"></a>Crontab ile ilgili yardım almak için

```bash
man crontab
```

### <a name="to-get-a-list-of-crontab-file-of-the-current-user"></a>Geçerli kullanıcının çapraz dosyasının listesini almak için

```bash
crontab -l
```

### <a name="to-get-a-list-of-crontab-file-of-another-user"></a>Başka bir kullanıcının çapraz dosyasının listesini almak için

```bash
crontab -u username -l
```

### <a name="to-backup-crontab-entries"></a>Çapraz girdileri yedeklemek için

```bash
crontab -l > /var/tmp/cron_backup.dat
```

> [!TIP]
> Düzenlemeden veya kaldırmadan önce bunu yapmak.

### <a name="to-restore-crontab-entries"></a>Çapraz girdileri geri yüklemek için

```bash
crontab /var/tmp/cron_backup.dat
```

### <a name="to-edit-the-crontab-and-add-a-new-job-as-a-root-user"></a>Kırpmayı düzenlemek ve kök kullanıcı olarak yeni iş eklemek için

```bash
sudo crontab -e
```

### <a name="to-edit-the-crontab-and-add-a-new-job"></a>Kırpmayı düzenlemek ve yeni iş eklemek için

```bash
crontab -e
```

### <a name="to-edit-other-users-crontab-entries"></a>Diğer kullanıcının çapraz girdilerini düzenlemek için

```bash
crontab -u username -e
```

### <a name="to-remove-all-crontab-entries"></a>Tüm çapraz girdileri kaldırmak için

```bash
crontab -r
```

### <a name="to-remove-other-users-crontab-entries"></a>Diğer kullanıcının çapraz girdilerini kaldırmak için

```bash
crontab -u username -r
```

### <a name="explanation"></a>Açıklama

<pre>
+—————- minute (values: 0 - 59) (special characters: , - * /)  <br>
| +————- hour (values: 0 - 23) (special characters: , - * /) <br>
| | +———- day of month (values: 1 - 31) (special characters: , - * / L W C)  <br>
| | | +——- month (values: 1 - 12) (special characters: ,- * / )  <br>
| | | | +—- day of week (values: 0 - 6) (Sunday=0 or 7) (special characters: , - * / L W C) <br>
| | | | |*****command to be executed
</pre>
