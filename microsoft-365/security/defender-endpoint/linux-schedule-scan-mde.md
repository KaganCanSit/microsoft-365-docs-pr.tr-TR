---
title: Uç nokta (Linux) için Microsoft Defender ile taramaları zamanlama
description: Kuruluş varlıklarını daha iyi korumak için Uç Nokta (Linux) için Microsoft Defender için otomatik tarama zamanı zamanlamayı öğrenin.
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
ms.openlocfilehash: ddb02d67866e675febda59fac15e8e494188a47f
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996526"
---
# <a name="schedule-scans-with-microsoft-defender-for-endpoint-linux"></a>Uç nokta (Linux) için Microsoft Defender ile taramaları zamanlama

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)


Linux için bir tarama çalıştırmak için bkz. [Desteklenen Komutlar](/microsoft-365/security/defender-endpoint/linux-resources#supported-commands).

Linux (ve Unix), zamanlanmış görevleri çalıştırabilecek **crontab** (Görev Zamanlayıcı gibi) adlı bir araciya sahip.

## <a name="pre-requisite"></a>Önkul

> [!NOTE]
> Tüm saat dilimlerinin listesini almak için aşağıdaki komutu çalıştırın: `timedatectl list-timezones`<br>
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
sudo crontab -l > /var/tmp/cron_backup_200919.dat
```

> [!NOTE]
> Burada 200919 == YRMMDD

> [!TIP]
> Düzenlemeden veya kaldırmadan önce bunu yapmak.

Kırpmayı düzenlemek ve kök kullanıcı olarak yeni bir iş eklemek için:

```bash
sudo crontab -e
```

> [!NOTE]
> Varsayılan düzenleyici VIM'dir.

Şunları da görüyor olabileceğiniz gibi:

```outbou
0 * * * * /etc/opt/microsoft/mdatp/logrorate.sh
```

"Ekle" tuşuna basın

Aşağıdaki girdileri ekleyin:

```bash
CRON_TZ=America/Los_Angeles

0 2 * * sat /bin/mdatp scan quick > ~/mdatp_cron_job.log
```

> [!NOTE]
> Bu örnekte, bunu 00 dakika ve 02:00 olarak ayarla kullandık. (24 saat biçiminde saat), ayın herhangi bir günü, herhangi bir ay, Cumartesi günleri. Bu, Cumartesi günü 02:00'de devam anlamına gelir. Pasifik (UTC -8).

"Esc" tuşuna basın

Çift tırnak`:wq` içinde "" yazın.

> [!NOTE]
> w == write, q == quit

İşlerinizi görüntülemek için `sudo crontab -l`

:::image type="content" source="../../media/linux-mdatp-1.png" alt-text="linux mdatp.":::

#### <a name="to-inspect-cron-job-runs"></a>İş ilanlarını incelemek için

```bash
sudo grep mdatp /var/log/cron
```

#### <a name="to-inspect-the-mdatp_cron_joblog"></a>mdatp_cron_job.log* dosyasını incelemek için

```bash
sudo nano mdatp_cron_job.log
```

## <a name="for-those-who-use-ansible-chef-or-puppet"></a>Ansible,Sina veya Yalçın'i kullananlar için

Aşağıdaki komutları kullanın:

### <a name="to-set-cron-jobs-in-ansible"></a>Ansible'da iş kırpmayı ayarlamak için

```bash
cron - Manage cron.d and crontab entries

See [https://docs.ansible.com/ansible/latest/modules/cron_module.html](https://docs.ansible.com/ansible/latest/modules/cron_module.html) for more information.

### To set crontabs in Chef

```bash
cron resource
```bash

```
Daha <https://docs.chef.io/resources/cron/> fazla bilgi için bkz.

### <a name="to-set-cron-jobs-in-puppet"></a>Jobs'ta iş kırpmayı ayarlamak için

```bash
Resource Type: cron
```

Daha <https://puppet.com/docs/puppet/5.5/types/cron.html> fazla bilgi için bkz.

Çiğdem: Cron işleri ve zamanlanmış görevlerle otomatik oluşturma

Daha [https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/](https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/) fazla bilgi için bkz.

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

+—————- dakika (değerler: 0 - 59) (özel karakterler: , - * /)  <br>
| +————- saat (değerler: 0 - 23) (özel karakterler: , - * /) <br>
| | +———- günü (değerler: 1 - 31) (özel karakterler: , - * / L W C)  <br>
| | | +——- ay (değerler: 1 - 12) (özel karakterler: ,- * / )  <br>
| | | | +—- haftanın günü (değerler: 0 - 6) (Pazar=0 veya 7) (özel karakterler: , - * / L W C) <br>
| | | | |*****komutu yürütüllecek
