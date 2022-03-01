---
title: Etkin olmayan posta kutusunu geri yükleme
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 97e06a7a-ef9a-4ce8-baea-18b9e20449a3
description: Etkin olmayan bir posta kutusunun içeriğini var olan bir posta kutusuna geri yükleme (veya birleştirme) hakkında bilgi alın.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: aaf0ce7f67ae0146beceeeb667263908d7cff75d
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010855"
---
# <a name="restore-an-inactive-mailbox"></a>Etkin olmayan posta kutusunu geri yükleme

Kuruluşundan ayrıldığında eski çalışanın e-postalarını tutmak için etkin olmayan posta kutusu (bu tür bir yumuşak silinmiş posta kutusudur) kullanılır. Başka bir çalışan, ayrılan çalışanın iş sorumluluklarını alırsa veya bu çalışan organizasyona dönerse, etkin olmayan posta kutusunun içeriğini kullanıcıya açık hale getirmenin iki yolu vardır:

- **Etkin olmayan posta kutusunu geri yükleme** Başka bir çalışan, ayrılan çalışanın iş sorumluluklarını alırsa veya başka bir kullanıcı etkin olmayan posta kutusunun içeriğine erişmesi gerekirse, etkin olmayan posta kutusunun içeriğini mevcut bir posta kutusuna geri yükleyebilir (veya birleştirebilirsiniz). Ayrıca, arşivi etkin olmayan bir posta kutusundan da geri yükleyebilirsiniz. Geri yüklendikten sonra, etkin olmayan posta kutusu korunur ve etkin olmayan posta kutusu olarak korunur. Bu konu başlığında, etkin olmayan posta kutusunu geri yükleme yordamları açıklanmıştır.

- **Etkin olmayan posta kutusunu kurtarma** Ayrılan çalışan organizasyona dönerse veya ayrılan çalışanın iş sorumluluklarını almak için işe yeni bir çalışan işe alındısa, etkin olmayan posta kutusunun içeriğini kurtarabilirsiniz. Bu yöntem, etkin olmayan posta kutusunu etkin olmayan posta kutusunun içeriğini içeren yeni bir posta kutusuna dönüştürür. Kurtarılan etkin olmayan posta kutusu artık yoktur. Adım adım yordamlar için bkz. Etkin olmayan [posta kutusunu posta kutusunda Office 365](recover-an-inactive-mailbox.md).

Etkin olmayan [bir posta](#more-information) kutusunu geri yükleme ve kurtarma arasındaki farklar hakkında daha ayrıntılı bilgi için bu makalenin Daha fazla bilgi bölümüne bakın.

> [!NOTE]
> Otomatik genişleyen bir arşivle yapılandırılmış etkin olmayan posta kutusunu kurtarılamaz veya geri yükleyebilirsiniz. Otomatik genişleyen bir arşivle etkin olmayan posta kutusundan verileri kurtarmanız gerekirse, içeriği arama özelliğini kullanarak verileri posta kutusundan dışarı aktarın ve sonra başka bir posta kutusuna aktarın. Yönergeler için aşağıdaki konulara bakın:
>
> - [İçerik arama](content-search.md)
> - [İçerik arama sonuçlarını dışarı aktarma](export-search-results.md)

## <a name="requirements-to-restore-an-inactive-mailbox"></a>Etkin olmayan posta kutusunu geri yükleme gereksinimleri

- Etkin olmayan bir posta Exchange Online geri yüklemek için PowerShell'i kullan gerekir. Exchange yönetim merkezini (EAC) kullanasınız. Adım adım yönergeler için bkz. [PowerShell'Bağlan Exchange Online kullanma](/powershell/exchange/connect-to-exchange-online-powershell).

- PowerShell'de Exchange Online etkin olmayan posta kutularının kimlik bilgilerini almak için bu komutu çalıştırın.

  ```powershell
  Get-Mailbox -InactiveMailboxOnly | Format-List Name,DistinguishedName,ExchangeGuid,PrimarySmtpAddress
  ```

  Etkin olmayan belirli bir posta kutusunu tanımlamak ve geri yüklemek için bu komutun döndürülen bilgilerini kullanın.

- Etkin olmayan posta kutuları hakkında daha fazla bilgi için bkz. Etkin [olmayan posta kutuları Office 365](inactive-mailboxes-in-office-365.md).

## <a name="restore-inactive-mailboxes"></a>Etkin olmayan posta kutularını geri yükleme

Etkin olmayan bir posta kutusunun içeriğini mevcut bir posta kutusuna geri yüklemek için **, New-MailboxRestoreRequest** cmdlet'ini  _SourceMailbox_ ve  _TargetMailbox_ parametreleriyle kullanın. Bu cmdlet'i kullanma hakkında daha fazla bilgi için bkz. [New-MailboxRestoreRequest](/powershell/module/exchange/new-mailboxrestorerequest).

Etkin olmayan bir posta kutusunu geri yükleymeden önce, etkin olmayan posta kutusunun LegacyExchangeDN'sini hedef posta kutusunun X500 ara sunucu adresi olarak hedef posta kutusuna eklemeniz gerekir. Bu yapılması gerekir, çünkü **New-MailboxRestoreRequest** cmdlet'i kaynak ve hedef posta kutuları üzerinde **LegacyExchangeDN özelliğinin değerinin** aynı olduğundan emin olmak için bunu denetler. Etkin olmayan posta kutusunu geri yükledikten sonra, isteğe bağlı olarak etkin olmayan posta kutusunun LegacyExchangeDN'sini kaynak posta kutusundan kaldırabilirsiniz. LegacyExchangeDN'yi kaldırmadan önce posta kutusu geri yükleme isteği tamamlandıktan sonra beklemeyi lütfen bekleyin.

Etkin olmayan bir posta kutusunu var olan bir posta kutusuna geri yüklemek için şu adımları izleyin:

1. Etkin olmayan posta kutusunun özelliklerini içeren bir değişken oluşturun.

   ```powershell
   $inactiveMailbox = Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox>
   ```

   > [!IMPORTANT]
   > Önceki komutta, etkin olmayan posta kutusunu tanımlamak için **DistinguishedName** veya **ExchangeGUID** özelliğinin değerini kullanın. Etkin ve etkin olmayan bir posta kutusunun aynı birincil SMTP adresine sahip olması mümkündür, ancak bu özellikler, organizasyonlu her posta kutusu için benzersizdir.

2. Etkin olmayan posta kutusunun LegacyExchangeDN'lerini görüntüleniyor ve sonraki adımda bunu hedef posta kutusuna ara sunucu adresi olarak  ekleyebilirsiniz.

   ```powershell
   $inactiveMailbox.LegacyExchangeDN
   ```

3. Etkin olmayan posta kutusunun LegacyExchangeDN'lerini hedef posta kutusuna bir X500 ara sunucu adresi olarak ekleyin.

   ```powershell
   Set-Mailbox <identity of target mailbox> -EmailAddresses @{Add="X500:<LegacyExchangeDN of inactive mailbox>"}
   ```

4. Etkin olmayan posta kutusunun içeriğini var olan bir posta kutusuna geri yükleme. Etkin olmayan posta kutusunun (kaynak posta kutusunun) içeriği, var olan posta kutusunda (hedef posta kutusu) ilgili klasörlerle birleştirilir.

   ```powershell
   New-MailboxRestoreRequest -SourceMailbox $inactiveMailbox.DistinguishedName -TargetMailbox <identity of target mailbox> 
   ```

   Alternatif olarak, etkin olmayan posta kutusundan içeriğini geri yüklemek için hedef posta kutusunda üst düzey bir klasör belirtebilirsiniz. Belirtilen hedef klasör veya hedef klasör yapısı hedef posta kutusunda önceden yoksa, geri yükleme işlemi sırasında oluşturulur.

   Bu örnekte, etkin olmayan bir posta kutusundan posta kutusu öğeleri ve alt klasörler hedef posta kutusunun en üst düzey klasör yapısında "Etkin Olmayan Posta Kutusu" adlı bir klasöre kopyalanır.

   ```powershell
   New-MailboxRestoreRequest -SourceMailbox $InactiveMailbox.DistinguishedName -TargetMailbox <identity of target mailbox> -TargetRootFolder "Inactive Mailbox"
   ```

5. Geri yükleme isteği tamamlandıktan sonra, isteğe bağlı olarak hedef posta kutusundan etkin olmayan posta kutusunun LegacyExchangeDN'sini kaldırabilirsiniz. LegacyExchangeDN'yi etkin olmayan posta kutusundan bırakmak hedef posta kutusunu etkilemez.

   ```powershell
   Set-Mailbox <identity of target mailbox> -EmailAddresses @{Remove="X500:<LegacyExchangeDN of inactive mailbox>"}
   ```

## <a name="restore-the-archive-from-an-inactive-mailbox"></a>Etkin olmayan bir posta kutusundan arşivi geri yükleme

Etkin olmayan bir posta kutusunun arşiv posta kutusu varsa, bu posta kutusunu var olan bir posta kutusunun arşiv posta kutusuna da geri yükleyebilirsiniz. Arşivi etkin olmayan bir posta kutusundan geri yüklemek için, _SourceIsArchive_ ve _TargetIsArchive_ anahtarlarını etkin olmayan bir posta kutusunu geri yüklemek için kullanılan komuta eklemeniz gerekir.

1. Etkin olmayan posta kutusunun özelliklerini içeren bir değişken oluşturun.

   ```powershell
   $inactiveMailbox = Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox>
   ```

   > [!NOTE]
   > Önceki komutta, etkin olmayan posta kutusunu tanımlamak için **DistinguishedName** veya **ExchangeGUID** özelliğinin değerini kullanın. Etkin ve etkin olmayan bir posta kutusunun aynı birincil SMTP adresine sahip olması mümkündür, ancak bu özellikler, organizasyonlu her posta kutusu için benzersizdir.

2. Etkin olmayan posta kutusunun LegacyExchangeDN'lerini görüntüleniyor ve sonraki adımda bunu hedef posta kutusuna ara sunucu adresi olarak  ekleyebilirsiniz.

   ```powershell
   $inactiveMailbox.LegacyExchangeDN
   ```

3. Etkin olmayan posta kutusunun LegacyExchangeDN'lerini hedef posta kutusuna bir X500 ara sunucu adresi olarak ekleyin.

   ```powershell
   Set-Mailbox <identity of target mailbox> -EmailAddresses @{Add="X500:<LegacyExchangeDN of inactive mailbox>"}
   ```

4. Arşivin içeriğini etkin olmayan posta kutusundan (kaynak arşiv) varolan bir posta kutusunun (hedef arşiv) arşivine geri yükleme. Bu örnekte, kaynak arşivdeki içerik hedef posta kutusunun arşivinde "Etkin Olmayan Posta Kutusu Arşivi" adlı bir klasöre kopyalanır.

   ```powershell
   New-MailboxRestoreRequest -SourceMailbox $InactiveMailbox.DistinguishedName -SourceIsArchive -TargetMailbox <identity of target mailbox> -TargetIsArchive -TargetRootFolder "Inactive Mailbox Archive"
   ```

5. Geri yükleme isteği tamamlandıktan sonra, isteğe bağlı olarak hedef posta kutusundan etkin olmayan posta kutusunun LegacyExchangeDN'sini kaldırabilirsiniz. LegacyExchangeDN'yi etkin olmayan posta kutusundan bırakmak hedef posta kutusunu etkilemez.

   ```powershell
   Set-Mailbox <identity of target mailbox> -EmailAddresses @{Remove="X500:<LegacyExchangeDN of inactive mailbox>"}
   ```

## <a name="more-information"></a>Daha fazla bilgi

- **Etkin olmayan posta kutusunu kurtarma ve geri yükleme arasındaki temel fark nedir?** Etkin olmayan bir posta kutusunu kurtarca, posta kutusu yeni bir posta kutusuna dönüştürülür. Etkin olmayan posta kutusunun içeriği ve klasör yapısı korunur ve posta kutusu yeni bir kullanıcı hesabına bağlıdır. Kurtarılan, etkin olmayan posta kutusu artık yoktur ve yeni posta kutusunun içeriğinde yapılan değişiklikler etkin olmayan posta kutusunda özgün olarak basılı durumda olan içeriği etkiler. Tersine, etkin olmayan bir posta kutusunu geri yüklemekle, içerikler yalnızca başka bir posta kutusuna kopyalanır. Etkin olmayan posta kutusu korunur ve etkin olmayan posta kutusu olarak kalır. Hedef posta kutusunda içerikte yapılan değişiklikler, etkin olmayan posta kutusundan alınan özgün içeriği etkilemez. Etkin olmayan posta kutusunda İçerik Arama aracı kullanılarak arama özelliği [kullanılabilir, içeriği](content-search.md) başka bir posta kutusuna geri yüklenebilir veya daha sonraki bir tarihte kurtarılabilir veya silinebilir.

- **Etkin olmayan posta kutularını nasıl bulursunuz?** Kuruluşta etkin olmayan posta kutularının listesini almak ve etkin olmayan bir posta kutusunu geri yüklemek için yararlı olan bilgileri görüntülemek için, bu komutu çalıştırabilirsiniz.

  ```powershell
  Get-Mailbox -InactiveMailboxOnly | Format-List Name,PrimarySMTPAddress,DistinguishedName,ExchangeGUID,LegacyExchangeDN,ArchiveStatus
  ```

- **Etkin olmayan Microsoft 365 bekletme ilkesi veya Mahkeme Tutma ya da etkin olmayan posta kutusu içeriğini tutmak için kullanın.** Geri yüklendikten sonra etkin olmayan posta kutusunun durumunu korumak için, hedef posta kutusuna [bir Microsoft 365](retention.md) bekletme ilkesi uygulayabilir veya etkin olmayan posta kutusunu geri yüklemeden önce hedef posta kutusunu [Mahkeme Tutma] (mahkeme tutma](hold.md oluştur)'a uygulayabilirsiniz. Bu, etkin olmayan posta kutusu olan öğelerin hedef posta kutusuna geri yüklendikten sonra kalıcı olarak silinmesini önler.

- **Etkin olmayan bir posta kutusunu geri yüklemeden önce hedef posta kutusunda bekletmeyi etkinleştirin.** Etkin olmayan bir posta kutusundan gelen posta kutusu öğeleri eski olabileceğinden, etkin olmayan bir posta kutusunu geri yüklemeden önce hedef posta kutusunda bekletmeyi etkinleştirmeyi düşünebilirsiniz. Bir posta kutusunu bekletmeyi bekletmeye bırakarak, bekletme süresi dolana kadar veya bekletme süresi dolana kadar, bu posta kutusuna atanmış olan bekletme ilkesi işlenmez. Bu, hedef posta kutusunun sahibine etkin olmayan posta kutusundan gelen eski iletileri yönetmesi için zaman verir. Aksi takdirde, bekletme ilkesi hedef posta kutusu için yapılandırılmış bekletme ayarlarına göre süresi dolmuş olan eski öğeleri silebilir (veya etkinse arşiv posta kutusuna taşı). Daha fazla bilgi için bkz[. Posta kutusunu bekletme için yerinde Exchange Online](/exchange/security-and-compliance/messaging-records-management/mailbox-retention-hold).

- **Etkin olmayan posta kutularına farklı geri yükleme New-MailboxRestoreRequest için New-MailboxRestoreRequest cmdlet'iyle birlikte başka parametreler kullanabilirsiniz.** Örneğin, etkin olmayan posta kutusundan gelen arşivi hedef posta kutusunun birincil posta kutusuna geri yüklemek için bu komutu çalıştırabilirsiniz.

  ```powershell
  New-MailboxRestoreRequest -SourceMailbox <inactive mailbox> -SourceIsArchive -TargetMailbox <target mailbox> -TargetRootFolder "Inactive Mailbox Archive"
  ```

  Bu komutu çalıştırarak etkin olmayan birincil posta kutusunu hedef posta kutusunun arşivine geri yükleyebilirsiniz.

  ```powershell
  New-MailboxRestoreRequest -SourceMailbox <inactive mailbox> -TargetMailbox <target mailbox> -TargetIsArchive -TargetRootFolder "Inactive Mailbox"
  ```

- **TargetRootFolder parametresi ne yapar?** Daha önce de belirtildiği gibi, **TargetRootFolder** parametresini kullanarak hedef posta kutusunda etkin olmayan posta kutusunun içeriğini geri yüklemek üzere klasör yapısının en üstünde (kök olarak da denir) bir klasör belirtebilirsiniz. Bu parametreyi kullanamıyorsanız, etkin olmayan posta kutusundan gelen posta kutusu öğeleri hedef posta kutusunun ilgili varsayılan klasörleriyle birleştirilir ve hedef posta kutusunun kökünde özel klasörler yeniden oluşturulur. Aşağıdaki çizimlerde, TargetRootFolder parametresinin kullanımıyla kullanımı arasındaki **farklar vurgulanır** .

  **TargetRootFolder parametresi kullanılmamışken hedef posta kutusunda klasör hiyerarşisi**

  ![TargetRootFolder parametresi kullanılmamış olduğunda ekran görüntüsü.](../media/76a759af-f483-4d1c-8cc7-243435b5562e.png)

  **TargetRootFolder parametresi kullanıldığında hedef posta kutusunda klasör hiyerarşisi**

  ![TargetRootFolder parametresi kullanıldığında ekran görüntüsü.](../media/300da592-7323-48db-b8a4-07012259d113.png)
