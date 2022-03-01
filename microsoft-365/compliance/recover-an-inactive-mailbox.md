---
title: Etkin olmayan posta kutusunu kurtarma
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
ms.assetid: 35d0ecdb-7cb0-44be-ad5c-69df2f8f8b25
ms.custom: seo-marvel-apr2020
description: Etkin olmayan posta kutusunu etkin olmayan posta kutusunun içeriğini içeren yeni bir posta kutusuna dönüştürerek Office 365 posta kutusunun içeriğini kurtarmayı öğrenin.
ms.openlocfilehash: ce09d218d86e7cd949da1df80cc75a19fce64159
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010857"
---
# <a name="recover-an-inactive-mailbox"></a>Etkin olmayan posta kutusunu kurtarma

Kuruluşundan ayrıldığında eski çalışanın e-postasını korumak için etkin olmayan posta kutusu (bu tür bir yumuşak silinmiş posta kutusudur) kullanılır. Çalışan organizasyona dönerse veya başka bir çalışan eski çalışanın iş sorumluluklarını alırsa, etkin olmayan posta kutusunun içeriğini kullanıcıya açık hale getirmenin iki yolu vardır:

- **Etkin olmayan posta kutusunu kurtarma.** Eski çalışan organizasyona dönerse veya yeni bir çalışan, eski çalışanın iş sorumluluklarını almak için işe alındısa, etkin olmayan posta kutusunun içeriğini kurtarabilirsiniz. Bu yöntem, etkin olmayan posta kutusunu etkin olmayan posta kutusunun içeriğini içeren yeni, etkin bir posta kutusuna dönüştürür. Kurtarılan etkin olmayan posta kutusu artık yoktur. Bu konudaki yordamlarda bu yöntem açıklanmıştır.

- **Etkin olmayan posta kutusunu geri yükleme.** Başka bir çalışan eski çalışanın iş sorumluluklarını alırsa veya başka bir kullanıcının etkin olmayan posta kutusunun içeriğine erişmesi gerekirse, etkin olmayan posta kutusunun içeriğini mevcut bir posta kutusuna geri yükleyebilir (veya birleştirebilirsiniz). Ayrıca, arşivi etkin olmayan bir posta kutusundan da geri yükleyebilirsiniz. Bu yönteme ilişkin yordamlar için bkz. Etkin [olmayan posta kutusunu şu Office 365](restore-an-inactive-mailbox.md).

Etkin olmayan [bir posta](#more-information) kutusunu kurtarma ve geri yükleme arasındaki farklar hakkında daha fazla bilgi ve etkin olmayan bir posta kutusu kurtarıldında ne olduğunu açıklama için Daha fazla bilgi bölümüne bakın.

> [!NOTE]
> Otomatik genişleyen bir arşivle yapılandırılmış etkin olmayan posta kutusunu kurtarılamaz veya geri yükleyebilirsiniz. Otomatik genişleyen bir arşivle etkin olmayan posta kutusundan verileri kurtarmanız gerekirse, içeriği arama özelliğini kullanarak verileri posta kutusundan dışarı aktarın ve sonra başka bir posta kutusuna aktarın. Yönergeler için aşağıdaki konulara bakın:
>
> - [İçerik arama](content-search.md)
> - [İçerik arama sonuçlarını dışarı aktarma](export-search-results.md)

## <a name="requirements-to-recover-an-inactive-mailbox"></a>Etkin olmayan posta kutusunu kurtarma gereksinimleri

- Etkin olmayan bir posta Exchange Online kurtarmak için PowerShell'i kullanabilirsiniz. Exchange yönetim merkezini (EAC) kullanasınız. Adım adım yönergeler için bkz. [PowerShell'Bağlan Exchange Online kullanma](/powershell/exchange/connect-to-exchange-online-powershell).

- Kuruluşta etkin olmayan posta kutularının kimlik bilgilerini almak için aşağıdaki komutu çalıştırın.

  ```powershell
  Get-Mailbox -InactiveMailboxOnly | Format-List Name,DistinguishedName,ExchangeGuid,PrimarySmtpAddress
  ```

  Etkin olmayan belirli bir posta kutusunu kurtarmak için bu komutun tarafından döndürülen bilgileri kullanın.

## <a name="recover-inactive-mailboxes"></a>Etkin olmayan posta kutularını kurtarma

Etkin olmayan **bir posta kutusunu kurtarmak için New-Mailbox** cmdlet'ini  *InactiveMailbox*  parametresiyle kullanın.

1. Etkin olmayan posta kutusunun özelliklerini içeren bir değişken oluşturun.

   ```powershell
   $InactiveMailbox = Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox>
   ```

   > [!IMPORTANT]
   > Önceki komutta, etkin olmayan posta kutusunu tanımlamak için **DistinguishedName** veya **ExchangeGUID** özelliğinin değerini kullanın. Etkin ve etkin olmayan bir posta kutusunun aynı birincil SMTP adresine sahip olması mümkündür, ancak bu özellikler, organizasyonlu her posta kutusu için benzersizdir.

2. Bu örnekte, önceki komutta alınan özellikler kullanılır ve etkin olmayan posta kutusu Ann Beebe kullanıcı için etkin bir posta kutusuna kurtarılır. *Name* ve *MicrosoftOnlineServicesID parametreleri için belirtilen değerlerin* kurum içinde benzersiz olduğundan emin olun.

   ```powershell
   New-Mailbox -InactiveMailbox $InactiveMailbox.DistinguishedName -Name annbeebe -FirstName Ann -LastName Beebe -DisplayName "Ann Beebe" -MicrosoftOnlineServicesID Ann.Beebe@contoso.com -Password (ConvertTo-SecureString -String 'P@ssw0rd' -AsPlainText -Force) -ResetPasswordOnNextLogon $true
   ```

   Kurtarılan etkin olmayan posta kutusunun birincil SMTP adresi  *, MicrosoftOnlineServicesID*  parametresi tarafından belirtilenle aynı değere sahip olur.

Etkin olmayan bir posta kutusunu kurtardikten sonra, yeni bir kullanıcı hesabı da oluşturulur. Lisans ataarak bu kullanıcı hesabını etkinleştirmeniz gerekir. Aynı anda lisans Microsoft 365 yönetim merkezi için bkz[. Kullanıcı ekleme ve lisans atama](../admin/add-users/add-users.md).

## <a name="more-information"></a>Daha fazla bilgi

- **Etkin olmayan posta kutusunu kurtarma ve geri yükleme arasındaki temel fark nedir?** Etkin olmayan bir posta kutusunu kurtarsanız, posta kutusu yeni bir posta kutusuna dönüştürülür, etkin olmayan posta kutusunun içeriği ve klasör yapısı korunur ve posta kutusu yeni bir kullanıcı hesabına bağlıdır. Kurtarılan, etkin olmayan posta kutusu artık yoktur ve yeni posta kutusunun içeriğinde yapılan değişiklikler etkin olmayan posta kutusunda özgün olarak basılı durumda olan içeriği etkiler. Tersine, etkin olmayan bir posta kutusunu geri yüklemekle, içerikler yalnızca başka bir posta kutusuna kopyalanır. Etkin olmayan posta kutusu korunur ve etkin olmayan posta kutusu olarak kalır. Hedef posta kutusunda içerikte yapılan değişiklikler, etkin olmayan posta kutusundan alınan özgün içeriği etkilemez. Etkin olmayan posta kutusunda, In-Place eBulma kullanılarak arama görünebilir, bu posta kutusunun içeriği başka bir posta kutusuna geri yüklenebilir veya daha sonraki bir tarihte kurtarılabilir veya silinebilir.

- **Etkin olmayan bir posta kutusunu kurtarca ne olur?** Etkin olmayan bir posta kutusunu kurtarca, aşağıdakiler gerçekleşir:

  - Etkin olmayan bir posta kutusuna uygulanan tutma, kurtarılmadan önce etkin olmayan posta kutusuna uygulanan tutma türüne bağlı olarak değiştirilir veya kaldırılır.

    - **Mahkeme Tutma.** Etkin olmayan posta kutusu için Mahkeme Tutma etkinleştirildiyse, kurtarılan posta kutusundan kaldırılır.

    - **Yerinde Tutma ve** In-Place, kurtarılan posta kutusundan kaldırılır. Bu, kurtarılan posta kutusunun herhangi bir eBulma aramalarından kaynak posta In-Place kaldırıldığı In-Place anlamına gelir.

    - **Microsoft 365 saklama ilkesi içerir.** Etkin olmayan posta kutusu Koruma Kilidi (kilitli bekletme ilkesi olarak adlandırılan) bir bekletme ilkesine atanmışsa *,* kurtarılan posta kutusu aynı kilitli bekletme ilkesine atanır. Kilitli bekletme ilkeleri hakkında daha fazla bilgi için bkz. [Bekletme ilkeleri ve bekletme etiketi ilkelerine yapılan değişiklikleri kısıtlamak için Koruma [Kilidi'ne bakın](retention-preservation-lock.md).

    - **Microsoft 365 Saklama Kilidi olmadan tutma ilkesi sağlar.** Etkin olmayan posta kutusu, ilkeye uygulanmış Microsoft 365 bir bekletme ilkesinden kaldırılır. Bununla birlikte, belirli bir yaştan daha eski içerikleri silen kuruluş genelindeki tüm bekletme ilkelerine göre posta kutusu içeriğinin silinmesini önlemek için, kurtarılan posta kutusunda Mahkeme Tutma etkindir. Mahkeme Tutma tutma veya kaldırma Daha fazla bilgi için [bkz. Mahkeme Tutma Oluşturma](create-a-litigation-hold.md).

  - Tek öğe kurtarma dönemi ( **retainDeletedItemsFor** posta kutusu özelliğiyle tanımlanır) 30 gün olarak ayarlanır. Normalde, posta kutusunda yeni bir posta Exchange Online oluşturulduğunda, bu bekletme süresi 14 gün olarak ayarlanır. Bu değeri 30 günlük en yüksek değere ayarlarsanız, kalıcı olarak silinmiş (veya temiz) etkin olmayan posta kutusundan kurtarılan tüm verileri kurtarmak için size daha fazla zaman verir. Ayrıca tek öğe kurtarmayı devre dışı bırakabilirsiniz veya tek öğe kurtarma dönemi varsayılan değere 14 gün geri dönebilirsiniz. Daha fazla bilgi için bkz. [Posta kutusu için tek öğe kurtarmayı etkinleştirme veya devre dışı bırakma](/exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-single-item-recovery).

  - Bekletme bekletme etkinleştirilir ve bekletme süresi 30 gün olarak ayarlanır. Bu, varsayılan bekletme Exchange ve yeni posta kutusuna atanan tüm kuruluş genelindeki Exchange veya Microsoft 365 bekletme ilkelerinin 30 gün süreyle işlenmez olduğu anlamına gelir. Bu, geri dönen çalışana veya kurtarılan etkin olmayan posta kutusunun yeni sahibine eski iletileri yönetme süresi verir. Aksi takdirde, Exchange veya Microsoft 365 bekletme ilkesi, Exchange veya Microsoft 365 bekletme ilkeleri için yapılandırılan ayarlara göre süresi dolmuş olan eski posta kutusu öğelerini silebilir (veya etkinse arşiv posta kutusuna Microsoft 365 olabilir). 30 gün sonra, bekletme bekletme süresinin sona erer, **RetentionHoldEnabled** posta kutusu özelliği **False** olarak ayarlanır ve Yönetilen Klasör Yardımcısı posta kutusuna atanan ilkeleri işlemeye başlar. Bu ek süreye ihtiyacınız yoksa bekletmeyi kaldırabilirsiniz. Alternatif olarak, **Set-Mailbox -EndDateForRetentionHold** komutunu kullanarak bekletme süresini artırabilirsiniz. Daha fazla bilgi için bkz [. Posta kutusunu bekletmeye saklama](/exchange/security-and-compliance/messaging-records-management/mailbox-retention-hold).

- **Etkin olmayan posta kutusunun özgün durumunu korumanız gerekirse, kurtarılan posta kutusunu bekleyin.** Yeni posta kutusu sahibinin veya bekletme ilkesinden, kurtarılan etkin olmayan posta kutusundan gelen tüm iletileri kalıcı olarak silmeden engellemek için, posta kutusunu Mahkeme Tutma'ya alabilirsiniz. Daha fazla bilgi için [bkz. Mahkeme Tutma Oluşturma](./create-a-litigation-hold.md).

- **Etkin olmayan bir posta kutusunu kurtarmak için hangi kullanıcı kimliğini kullanabilirsiniz?** Etkin olmayan bir posta kutusunu kurtarıyorken,  *MicrosoftOnlineServicesID*  parametresi için belirttiğiniz değer etkin olmayan posta kutusuyla ilişkilendirilmiş özgün posta kutusundan farklı olabilir. Özgün kullanıcı kimliğini de kullanabilirsiniz. Ancak daha önce de belirtildiği gibi, etkin olmayan posta kutusunu kurtarıyorken  *Name*  ve  *MicrosoftOnlineServicesID*  için kullanılan değerlerin benzersiz olduğundan emin olun.

- **Etkin olmayan posta kutusunun posta kutusu bekletme süresi henüz dolmamışsa ne olur?** Etkin olmayan posta kutusu 30 gün önce yazılımla silinmişse, kurtarmak için **New-Mailbox -InactiveMailbox** komutunu kullanaabilirsiniz. İlgili kullanıcı hesabını geri yükleyerek kurtarmanız gerekir. Daha fazla bilgi için bkz [. Kuruluştan kullanıcı silme](../admin/add-users/delete-a-user.md).

- **Etkin olmayan bir posta kutusu için yumuşak silinmiş posta kutusu bekletme süresinin sona erdikten sonra ne olduğunu nasıl bilebilirsiniz?** Aşağıdaki komutu çalıştırın.

  ```powershell
  Get-Mailbox -InactiveMailboxOnly <identity of inactive mailbox> | Format-List ExternalDirectoryObjectId
  ```

  **ExternalDirectoryObjectId** özelliği için değer yoksa, posta kutusu bekletme süresinin süresi dolmaktadır ve **New-Mailbox -InactiveMailbox** komutunu çalıştırarak etkin olmayan posta kutusunu kurtarabilirsiniz. **ExternalDirectoryObjectId** özelliği için bir değer varsa, geçici silinmiş posta kutusu bekletme süresinin süresi dolmamış olabilir ve kullanıcı hesabını geri yükleyerek posta kutusunu kurtarmanız gerekir. Bkz [. Kuruluştan kullanıcı silme](../admin/add-users/delete-a-user.md).

- **Etkin olmayan bir posta kutusunu kurtardikten sonra arşiv posta kutusunu etkinleştirmeyi göz önünde bulundurabilirsiniz.** Bu, geri dönen kullanıcının veya yeni çalışanın eski iletileri arşiv posta kutusuna taşımalarına olanak sağlar. Bekletme süresinin dolması ile birlikte, varsayılan Exchange posta kutularına atanan Exchange Online Exchange arşiv ilkesi, iki yıllık veya daha eski öğeleri arşiv posta kutusuna taşıyecektir. Arşiv posta kutusunu etkinleştirmezsiniz, iki yıllık öğeler kullanıcının birincil posta kutusunda kalır. Daha fazla bilgi için bkz [. Arşiv posta kutularını etkinleştirme](enable-archive-mailboxes.md).