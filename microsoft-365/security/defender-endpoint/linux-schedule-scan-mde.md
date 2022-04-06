---
title: Uç Nokta için Microsoft Defender (Linux) ile tarama zamanlama
description: Kuruluşunuzun varlıklarını daha iyi korumak için Uç Nokta için Microsoft Defender (Linux) için otomatik tarama süresi zamanlamayı öğrenin.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, linux, scans, virüsten koruma, uç nokta için microsoft defender (linux)
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
ms.openlocfilehash: 706284ed0adf49c4da6357b6bb8217d5a14268e1
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663500"
---
# <a name="schedule-scans-with-microsoft-defender-for-endpoint-linux"></a>Uç Nokta için Microsoft Defender (Linux) ile tarama zamanlama

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)


Linux taraması çalıştırmak için bkz [. Desteklenen Komutlar](/microsoft-365/security/defender-endpoint/linux-resources#supported-commands).

Linux (ve Unix), zamanlanmış görevleri çalıştırabilmek için **crontab** (Görev Zamanlayıcı'ya benzer) adlı bir arağa sahiptir.

## <a name="pre-requisite"></a>Ön koşul

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

### <a name="backup-crontab-entries"></a>Crontab girdilerini yedekleme

```bash
sudo crontab -l > /var/tmp/cron_backup_200919.dat
```

> [!NOTE]
> Where 200919 == YRMMDD

> [!TIP]
> Düzenlemeden veya kaldırmadan önce bunu yapın.

Crontab'ı düzenlemek ve kök kullanıcı olarak yeni bir iş eklemek için:

```bash
sudo crontab -e
```

> [!NOTE]
> Varsayılan düzenleyici VIM'dir.

Şunu görebilirsiniz:

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
> Bu örnekte bunu 00 dakika ( 00:00) olarak ayarladık. (24 saat biçimindeki saat), ayın herhangi bir günü, herhangi bir ay, Cumartesi günleri. Yani cumartesileri saat 02:00'de çalışacak. Pasifik (UTC -8).

"Esc" tuşuna basın

Çift tırnak işareti olmadan "`:wq`" yazın.

> [!NOTE]
> w == write, q == quit

Cron işlerinizi görüntülemek için `sudo crontab -l`

:::image type="content" source="../../media/linux-mdatp-1.png" alt-text="Linux mdatp sayfası" lightbox="../../media/linux-mdatp-1.png":::

#### <a name="to-inspect-cron-job-runs"></a>Cron iş çalıştırmalarını incelemek için

```bash
sudo grep mdatp /var/log/cron
```

#### <a name="to-inspect-the-mdatp_cron_joblog"></a>mdatp_cron_job.log* dosyasını incelemek için

```bash
sudo nano mdatp_cron_job.log
```

## <a name="for-those-who-use-ansible-chef-or-puppet"></a>Ansible, Chef veya Puppet kullananlar için

Aşağıdaki komutları kullanın:

### <a name="to-set-cron-jobs-in-ansible"></a>Ansible'da cron işleri ayarlamak için

```bash
cron - Manage cron.d and crontab entries

See [https://docs.ansible.com/ansible/latest/modules/cron_module.html](https://docs.ansible.com/ansible/latest/modules/cron_module.html) for more information.

### To set crontabs in Chef

```bash
cron resource
```bash

```
Daha fazla bilgi için bkz <https://docs.chef.io/resources/cron/> .

### <a name="to-set-cron-jobs-in-puppet"></a>Puppet'da cron işleri ayarlamak için

```bash
Resource Type: cron
```

Daha fazla bilgi için bkz <https://puppet.com/docs/puppet/5.5/types/cron.html> .

Puppet: Cron işleri ve zamanlanmış görevler ile otomatikleştirme

Daha fazla bilgi için bkz [https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/](https://puppet.com/blog/automating-puppet-cron-jobs-and-scheduled-tasks/) .

## <a name="additional-information"></a>Ek bilgiler

### <a name="to-get-help-with-crontab"></a>Crontab ile ilgili yardım almak için

```bash
man crontab
```

### <a name="to-get-a-list-of-crontab-file-of-the-current-user"></a>Geçerli kullanıcının crontab dosyasının listesini almak için

```bash
crontab -l
```

### <a name="to-get-a-list-of-crontab-file-of-another-user"></a>Başka bir kullanıcının crontab dosyasının listesini almak için

```bash
crontab -u username -l
```

### <a name="to-backup-crontab-entries"></a>Crontab girdilerini yedeklemek için

```bash
crontab -l > /var/tmp/cron_backup.dat
```

> [!TIP]
> Düzenlemeden veya kaldırmadan önce bunu yapın.

### <a name="to-restore-crontab-entries"></a>Crontab girdilerini geri yüklemek için

```bash
crontab /var/tmp/cron_backup.dat
```

### <a name="to-edit-the-crontab-and-add-a-new-job-as-a-root-user"></a>Crontab'ı düzenlemek ve kök kullanıcı olarak yeni bir iş eklemek için

```bash
sudo crontab -e
```

### <a name="to-edit-the-crontab-and-add-a-new-job"></a>Crontab'ı düzenlemek ve yeni bir iş eklemek için

```bash
crontab -e
```

### <a name="to-edit-other-users-crontab-entries"></a>Diğer kullanıcının crontab girdilerini düzenlemek için

```bash
crontab -u username -e
```

### <a name="to-remove-all-crontab-entries"></a>Tüm crontab girdilerini kaldırmak için

```bash
crontab -r
```

### <a name="to-remove-other-users-crontab-entries"></a>Diğer kullanıcının crontab girdilerini kaldırmak için

```bash
crontab -u username -r
```

### <a name="explanation"></a>Açıklama

+—————- dakika (değerler: 0 - 59) (özel karakterler: , \- \* /)  <br>
| +————- saat (değerler: 0 - 23) (özel karakterler: , \- \* /) <br>
| | +———- ayın günü (değerler: 1 - 31) (özel karakterler: , \- \* / L W C)  <br>
| | | +——- ay (değerler: 1 - 12) (özel karakterler: , \- \* / )  <br>
| | | | +—- haftanın günü (değerler: 0 - 6) (Pazar=0 veya 7) (özel karakterler: , \- \* / L W C) <br>
yürütülecek | | | | |****komut
