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
description: Etkin olmayan bir posta kutusunun içeriğini mevcut posta kutusuna geri yüklemeyi (veya birleştirmeyi) öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 66f9e75a76b4fb1bda0f9ae0f70cfe12c816d2bb
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65438235"
---
# <a name="restore-an-inactive-mailbox"></a>Etkin olmayan posta kutusunu geri yükleme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Etkin olmayan bir posta kutusu (geçici olarak silinen posta kutusu türüdür) kuruluşunuzdan ayrıldıktan sonra eski bir çalışanın e-postasını tutmak için kullanılır. Başka bir çalışan, ayrılan çalışanın iş sorumluluklarını üstlenirse veya bu çalışan kuruluşunuza geri dönerse, etkin olmayan posta kutusunun içeriğini kullanıcının kullanımına sunmanın iki yolu vardır:

- **Etkin olmayan posta kutusunu geri yükleme** Başka bir çalışan, ayrılan çalışanın iş sorumluluklarını üstlenirse veya başka bir kullanıcının etkin olmayan posta kutusunun içeriğine erişmesi gerekiyorsa, etkin olmayan posta kutusunun içeriğini mevcut bir posta kutusuna geri yükleyebilir (veya birleştirebilirsiniz). Ayrıca, etkin olmayan bir posta kutusundan arşivi geri yükleyebilirsiniz. Geri yüklendikten sonra, etkin olmayan posta kutusu korunur ve etkin olmayan posta kutusu olarak korunur. Bu makalede, etkin olmayan posta kutusunu geri yükleme yordamları açıklanmaktadır.

- **Etkin olmayan posta kutusunu kurtarma** Ayrılan çalışan kuruluşunuza geri dönerse veya ayrılan çalışanın iş sorumluluklarını üstlenmesi için yeni bir çalışan işe alınırsa, etkin olmayan posta kutusunun içeriğini kurtarabilirsiniz. Bu yöntem, etkin olmayan posta kutusunu, etkin olmayan posta kutusunun içeriğini içeren yeni bir posta kutusuna dönüştürür. Kurtarıldıktan sonra, etkin olmayan posta kutusu artık yok. Adım adım yordamlar için bkz. [Office 365'da etkin olmayan posta kutusunu kurtarma](recover-an-inactive-mailbox.md).

Etkin olmayan posta kutusunu geri yükleme ve kurtarma arasındaki farklar hakkında daha fazla bilgi için bu makaledeki [Daha fazla bilgi](#more-information) bölümüne bakın.

> [!NOTE]
> Otomatik olarak genişletilen arşivle yapılandırılmış etkin olmayan bir posta kutusunu kurtaramaz veya geri yükleyemezsiniz. Otomatik olarak genişleten bir arşive sahip etkin olmayan bir posta kutusundan veri kurtarmanız gerekiyorsa, verileri posta kutusundan dışarı aktarmak ve sonra başka bir posta kutusuna aktarmak için içerik aramasını kullanın. Yönergeler için aşağıdaki makalelere bakın:
>
> - [İçerik arama](content-search.md)
> - [İçerik arama sonuçlarını dışarı aktarma](export-search-results.md)

## <a name="requirements-to-restore-an-inactive-mailbox"></a>Etkin olmayan posta kutusunu geri yükleme gereksinimleri

- Etkin olmayan bir posta kutusunu geri yüklemek için powershell Exchange Online kullanmanız gerekir. Bu yordam için Exchange yönetim merkezini (EAC) veya Microsoft Purview uyumluluk portalı kullanamazsınız. Exchange Online PowerShell'i kullanmaya yönelik adım adım yönergeler için bkz. [PowerShell'i Exchange Online için Bağlan](/powershell/exchange/connect-to-exchange-online-powershell).

- Kuruluşunuzdaki etkin olmayan posta kutularına ilişkin kimlik bilgilerini almak için powershell Exchange Online aşağıdaki komutu çalıştırın.

  ```powershell
  Get-Mailbox -InactiveMailboxOnly | Format-List Name,DistinguishedName,ExchangeGuid,PrimarySmtpAddress
  ```

  Belirli bir etkin olmayan posta kutusunu tanımlamak ve geri yüklemek için bu komut tarafından döndürülen bilgileri kullanın.

- Etkin olmayan posta kutuları hakkında daha fazla bilgi için bkz. [Office 365'da etkin olmayan posta kutuları](inactive-mailboxes-in-office-365.md).

## <a name="restore-inactive-mailboxes"></a>Etkin olmayan posta kutularını geri yükleme

Etkin olmayan posta kutusunun içeriğini var olan bir posta kutusuna geri yüklemek için _SourceMailbox_ ve _TargetMailbox_ parametreleriyle **New-MailboxRestoreRequest** cmdlet'ini kullanın. Bu cmdlet'i kullanma hakkında daha fazla bilgi için bkz. [New-MailboxRestoreRequest](/powershell/module/exchange/new-mailboxrestorerequest).

Etkin olmayan posta kutusunu geri yükleyebilmeniz için önce etkin olmayan posta kutusunun LegacyExchangeDN'sini hedef posta kutusuna hedef posta kutusunun X500 proxy adresi olarak eklemeniz gerekir. **New-MailboxRestoreRequest** cmdlet'i, kaynak ve hedef posta kutularındaki **LegacyExchangeDN özelliğinin değerinin** aynı olduğundan emin olmak için denetler. Etkin olmayan posta kutusunu geri yükledikten sonra, isteğe bağlı olarak etkin olmayan posta kutusunun LegacyExchangeDN'sini kaynak posta kutusundan kaldırabilirsiniz. LegacyExchangeDN'yi kaldırmadan önce posta kutusu geri yükleme isteğinin tamamlanmasını beklemeyi unutmayın.

Etkin olmayan bir posta kutusunu mevcut bir posta kutusuna geri yüklemek için şu adımları izleyin:

1. Etkin olmayan posta kutusunun özelliklerini içeren bir değişken oluşturun.

   ```powershell
   $inactiveMailbox = Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox>
   ```

   > [!IMPORTANT]
   > Önceki komutta, etkin olmayan posta kutusunu tanımlamak için **DistinguishedName** veya **ExchangeGUID** özelliğinin değerini kullanın. Bu özellikler kuruluşunuzdaki her posta kutusu için benzersizdir ancak etkin ve etkin olmayan bir posta kutusunun aynı birincil SMTP adresine sahip olması mümkündür.

2. Etkin olmayan posta kutusunun LegacyExchangeDN'sini görüntüleyerek sonraki adımda bunu hedef posta kutusuna proxy adresi olarak ekleyebilirsiniz.

   ```powershell
   $inactiveMailbox.LegacyExchangeDN
   ```

3. Etkin olmayan posta kutusunun LegacyExchangeDN'sini hedef posta kutusuna X500 proxy adresi olarak ekleyin.

   ```powershell
   Set-Mailbox <identity of target mailbox> -EmailAddresses @{Add="X500:<LegacyExchangeDN of inactive mailbox>"}
   ```

4. Etkin olmayan posta kutusunun içeriğini mevcut bir posta kutusuna geri yükleyin. Etkin olmayan posta kutusunun (kaynak posta kutusu) içeriği, mevcut posta kutusunda (hedef posta kutusu) karşılık gelen klasörlerle birleştirilir.

   ```powershell
   New-MailboxRestoreRequest -SourceMailbox $inactiveMailbox.DistinguishedName -TargetMailbox <identity of target mailbox> 
   ```

   Alternatif olarak, hedef posta kutusunda etkin olmayan posta kutusundan içeriğin geri yükleneceği bir üst düzey klasör belirtebilirsiniz. Belirtilen hedef klasör veya hedef klasör yapısı hedef posta kutusunda zaten yoksa, geri yükleme işlemi sırasında oluşturulur.

   Bu örnek, posta kutusu öğelerini ve alt klasörlerini etkin olmayan bir posta kutusundan hedef posta kutusunun en üst düzey klasör yapısındaki "Etkin Olmayan Posta Kutusu" adlı klasöre kopyalar.

   ```powershell
   New-MailboxRestoreRequest -SourceMailbox $InactiveMailbox.DistinguishedName -TargetMailbox <identity of target mailbox> -TargetRootFolder "Inactive Mailbox"
   ```

5. Geri yükleme isteği tamamlandıktan sonra, isteğe bağlı olarak etkin olmayan posta kutusunun LegacyExchangeDN'sini hedef posta kutusundan kaldırabilirsiniz. LegacyExchangeDN'nin etkin olmayan posta kutusundan bırakılması hedef posta kutusunu etkilemez.

   ```powershell
   Set-Mailbox <identity of target mailbox> -EmailAddresses @{Remove="X500:<LegacyExchangeDN of inactive mailbox>"}
   ```

## <a name="restore-the-archive-from-an-inactive-mailbox"></a>Etkin olmayan posta kutusundan arşivi geri yükleme

Etkin olmayan bir posta kutusunun arşiv posta kutusu varsa, bunu mevcut bir posta kutusunun arşiv posta kutusuna da geri yükleyebilirsiniz. Arşivi etkin olmayan bir posta kutusundan geri yüklemek için _SourceIsArchive_ ve _TargetIsArchive_ anahtarlarını etkin olmayan posta kutusunu geri yüklemek için kullanılan komuta eklemeniz gerekir.

1. Etkin olmayan posta kutusunun özelliklerini içeren bir değişken oluşturun.

   ```powershell
   $inactiveMailbox = Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox>
   ```

   > [!NOTE]
   > Önceki komutta, etkin olmayan posta kutusunu tanımlamak için **DistinguishedName** veya **ExchangeGUID** özelliğinin değerini kullanın. Bu özellikler kuruluşunuzdaki her posta kutusu için benzersizdir ancak etkin ve etkin olmayan bir posta kutusunun aynı birincil SMTP adresine sahip olması mümkündür.

2. Etkin olmayan posta kutusunun LegacyExchangeDN'sini görüntüleyerek sonraki adımda bunu hedef posta kutusuna proxy adresi olarak ekleyebilirsiniz.

   ```powershell
   $inactiveMailbox.LegacyExchangeDN
   ```

3. Etkin olmayan posta kutusunun LegacyExchangeDN'sini hedef posta kutusuna X500 proxy adresi olarak ekleyin.

   ```powershell
   Set-Mailbox <identity of target mailbox> -EmailAddresses @{Add="X500:<LegacyExchangeDN of inactive mailbox>"}
   ```

4. Etkin olmayan posta kutusundan (kaynak arşiv) arşivin içeriğini mevcut posta kutusunun (hedef arşiv) arşivine geri yükleyin. Bu örnekte, kaynak arşivdeki içerik, hedef posta kutusunun arşivindeki "Etkin Olmayan Posta Kutusu Arşivi" adlı klasöre kopyalanır.

   ```powershell
   New-MailboxRestoreRequest -SourceMailbox $InactiveMailbox.DistinguishedName -SourceIsArchive -TargetMailbox <identity of target mailbox> -TargetIsArchive -TargetRootFolder "Inactive Mailbox Archive"
   ```

5. Geri yükleme isteği tamamlandıktan sonra, isteğe bağlı olarak etkin olmayan posta kutusunun LegacyExchangeDN'sini hedef posta kutusundan kaldırabilirsiniz. LegacyExchangeDN'nin etkin olmayan posta kutusundan bırakılması hedef posta kutusunu etkilemez.

   ```powershell
   Set-Mailbox <identity of target mailbox> -EmailAddresses @{Remove="X500:<LegacyExchangeDN of inactive mailbox>"}
   ```

## <a name="more-information"></a>Daha fazla bilgi

- **Etkin olmayan posta kutusunu kurtarma ve geri yükleme arasındaki temel fark nedir?** Etkin olmayan bir posta kutusunu kurtardığınızda, posta kutusu yeni bir posta kutusuna dönüştürülür. Etkin olmayan posta kutusunun içeriği ve klasör yapısı korunur ve posta kutusu yeni bir kullanıcı hesabına bağlanır. Kurtarıldıktan sonra, etkin olmayan posta kutusu artık yoktur ve yeni posta kutusunda içerikte yapılan değişiklikler, başlangıçta etkin olmayan posta kutusunda ayrı tutulmuş olan içeriği etkiler. Buna karşılık, etkin olmayan bir posta kutusunu geri yüklerken, içerik yalnızca başka bir posta kutusuna kopyalanır. Etkin olmayan posta kutusu korunur ve etkin olmayan bir posta kutusu olarak kalır. Hedef posta kutusunda içerikte yapılan değişiklikler, etkin olmayan posta kutusunda tutulan özgün içeriği etkilemez. Etkin olmayan posta kutusu [yine İçerik Arama aracı](content-search.md) kullanılarak aranabilir, içeriği başka bir posta kutusuna geri yüklenebilir veya daha sonraki bir tarihte kurtarılabilir veya silinebilir.

- **Etkin olmayan posta kutularını nasıl bulabilirsiniz?** Kuruluşunuzdaki etkin olmayan posta kutularının listesini almak ve etkin olmayan posta kutusunu geri yüklemek için yararlı olan bilgileri görüntülemek için bu komutu çalıştırabilirsiniz.

  ```powershell
  Get-Mailbox -InactiveMailboxOnly | Format-List Name,PrimarySMTPAddress,DistinguishedName,ExchangeGUID,LegacyExchangeDN,ArchiveStatus
  ```

- **Etkin olmayan posta kutusu içeriğini korumak için bir Microsoft 365 bekletme ilkesi veya Dava Bekletmesi kullanın.** Geri yüklendikten sonra etkin olmayan posta kutusunun durumunu korumak istiyorsanız, etkin olmayan posta kutusunu geri yüklemeden önce hedef posta kutusuna [bir Microsoft 365 bekletme ilkesi](retention.md) uygulayabilir veya hedef posta kutusunu [Dava Tutma'ya](create-a-litigation-hold.md) yerleştirebilirsiniz. Bu, tüm öğelerin hedef posta kutusuna geri yüklendikten sonra etkin olmayan posta kutusundan kalıcı olarak silinmesini engeller.

- **Etkin olmayan bir posta kutusunu geri yüklemeden önce hedef posta kutusunda bekletmeyi etkinleştirin.** Etkin olmayan posta kutusundan gelen posta kutusu öğeleri eski olabileceğinden, etkin olmayan posta kutusunu geri yüklemeden önce hedef posta kutusunda bekletmeyi etkinleştirmeyi düşünebilirsiniz. Bir posta kutusunu bekletme saklamaya aldığınızda, kendisine atanan bekletme ilkesi bekletme saklama kaldırılana kadar veya bekletme saklama süresi dolana kadar işlenmez. Bu, hedef posta kutusunun sahibine etkin olmayan posta kutusundan eski iletileri yönetme süresi verir. Aksi takdirde bekletme ilkesi, hedef posta kutusu için yapılandırılan bekletme ayarlarına bağlı olarak süresi dolmuş eski öğeleri silebilir (veya öğeleri arşiv posta kutusuna taşıyabilir). Daha fazla bilgi için bkz[. Exchange Online bekletme bekletmeye posta kutusu yerleştirme](/exchange/security-and-compliance/messaging-records-management/mailbox-retention-hold).

- **Etkin olmayan posta kutuları için farklı geri yükleme senaryoları uygulamak için New-MailboxRestoreRequest cmdlet'i ile diğer parametreleri kullanabilirsiniz.** Örneğin, etkin olmayan posta kutusundan arşivi hedef posta kutusunun birincil posta kutusuna geri yüklemek için bu komutu çalıştırabilirsiniz.

  ```powershell
  New-MailboxRestoreRequest -SourceMailbox <inactive mailbox> -SourceIsArchive -TargetMailbox <target mailbox> -TargetRootFolder "Inactive Mailbox Archive"
  ```

  Bu komutu çalıştırarak etkin olmayan birincil posta kutusunu hedef posta kutusunun arşivine de geri yükleyebilirsiniz.

  ```powershell
  New-MailboxRestoreRequest -SourceMailbox <inactive mailbox> -TargetMailbox <target mailbox> -TargetIsArchive -TargetRootFolder "Inactive Mailbox"
  ```

- **TargetRootFolder parametresi ne yapar?** Daha önce açıklandığı gibi **TargetRootFolder** parametresini kullanarak etkin olmayan posta kutusunun içeriğinin geri yükleneceği hedef posta kutusunda klasör yapısının üst kısmında (kök olarak da adlandırılır) bir klasör belirtebilirsiniz. Bu parametreyi kullanmıyorsanız, etkin olmayan posta kutusundan gelen posta kutusu öğeleri hedef posta kutusunun karşılık gelen varsayılan klasörleriyle birleştirilir ve özel klasörler hedef posta kutusunun kökünde yeniden oluşturulur. Aşağıdaki çizimlerde **, TargetRootFolder** parametresini kullanmama ve kullanma arasındaki bu farklar vurgulanır.

  **TargetRootFolder parametresi kullanılmadığında hedef posta kutusunda klasör hiyerarşisi**

  ![TargetRootFolder parametresi kullanılmadığında ekran görüntüsü.](../media/76a759af-f483-4d1c-8cc7-243435b5562e.png)

  **TargetRootFolder parametresi kullanıldığında hedef posta kutusunda klasör hiyerarşisi**

  ![TargetRootFolder parametresi kullanıldığında ekran görüntüsü.](../media/300da592-7323-48db-b8a4-07012259d113.png)
