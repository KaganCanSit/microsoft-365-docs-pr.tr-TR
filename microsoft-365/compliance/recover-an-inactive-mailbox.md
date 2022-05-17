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
description: etkin olmayan posta kutusunun içeriğini içeren yeni bir posta kutusuna dönüştürerek Office 365'da etkin olmayan posta kutusunun içeriğini kurtarmayı öğrenin.
ms.openlocfilehash: 027abe49a6e517a783f6458013bdcb4d0faee78b
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65435401"
---
# <a name="recover-an-inactive-mailbox"></a>Etkin olmayan posta kutusunu kurtarma

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Etkin olmayan bir posta kutusu (geçici olarak silinen posta kutusu türüdür) kuruluşunuzdan ayrıldıktan sonra eski bir çalışanın e-postasını korumak için kullanılır. Bu çalışan kuruluşunuza geri dönerse veya başka bir çalışan eski çalışanın iş sorumluluklarını üstlenirse, etkin olmayan posta kutusunun içeriğini kullanıcının kullanımına sunmanın iki yolu vardır:

- **Etkin olmayan bir posta kutusunu kurtarma.** Eski çalışan kuruluşunuza geri dönerse veya eski çalışanın iş sorumluluklarını üstlenmesi için yeni bir çalışan işe alınırsa, etkin olmayan posta kutusunun içeriğini kurtarabilirsiniz. Bu yöntem, etkin olmayan posta kutusunu, etkin olmayan posta kutusunun içeriğini içeren yeni, etkin bir posta kutusuna dönüştürür. Kurtarıldıktan sonra, etkin olmayan posta kutusu artık yok. Bu makaledeki yordamlarda bu yöntem açıklanmaktadır.

- **Etkin olmayan posta kutusunu geri yükleme.** Başka bir çalışan eski çalışanın iş sorumluluklarını üstlenirse veya başka bir kullanıcının etkin olmayan posta kutusunun içeriğine erişmesi gerekiyorsa, etkin olmayan posta kutusunun içeriğini mevcut bir posta kutusuna geri yükleyebilir (veya birleştirebilirsiniz). Ayrıca, etkin olmayan bir posta kutusundan arşivi geri yükleyebilirsiniz. Bu yöntemin yordamları için bkz. [Office 365'da etkin olmayan posta kutusunu geri yükleme](restore-an-inactive-mailbox.md).

Etkin olmayan bir posta kutusunu kurtarma ve geri yükleme arasındaki farklar hakkında daha fazla bilgi ve etkin olmayan bir posta kutusu kurtarıldığında ne olacağının açıklaması için [Daha fazla bilgi](#more-information) bölümüne bakın.

> [!NOTE]
> Otomatik olarak genişletilen arşivle yapılandırılmış etkin olmayan bir posta kutusunu kurtaramaz veya geri yükleyemezsiniz. Otomatik olarak genişleten bir arşive sahip etkin olmayan bir posta kutusundan veri kurtarmanız gerekiyorsa, verileri posta kutusundan dışarı aktarmak ve sonra başka bir posta kutusuna aktarmak için içerik aramasını kullanın. Yönergeler için aşağıdaki makalelere bakın:
>
> - [İçerik arama](content-search.md)
> - [İçerik arama sonuçlarını dışarı aktarma](export-search-results.md)

## <a name="requirements-to-recover-an-inactive-mailbox"></a>Etkin olmayan posta kutusunu kurtarma gereksinimleri

- Etkin olmayan bir posta kutusunu kurtarmak için powershell Exchange Online kullanmanız gerekir. Bu yordam için Exchange yönetim merkezini (EAC) veya Microsoft Purview uyumluluk portalı kullanamazsınız. Exchange Online PowerShell'i kullanmaya yönelik adım adım yönergeler için bkz. [PowerShell'i Exchange Online için Bağlan](/powershell/exchange/connect-to-exchange-online-powershell).

- Kuruluşunuzdaki etkin olmayan posta kutularının kimlik bilgilerini almak için aşağıdaki komutu çalıştırın.

  ```powershell
  Get-Mailbox -InactiveMailboxOnly | Format-List Name,DistinguishedName,ExchangeGuid,PrimarySmtpAddress
  ```

  Belirli bir etkin olmayan posta kutusunu kurtarmak için bu komut tarafından döndürülen bilgileri kullanın.

## <a name="recover-inactive-mailboxes"></a>Etkin olmayan posta kutularını kurtarma

Etkin olmayan posta kutusunu kurtarmak için *InactiveMailbox* parametresiyle **New-Mailbox** cmdlet'ini kullanın.

1. Etkin olmayan posta kutusunun özelliklerini içeren bir değişken oluşturun.

   ```powershell
   $InactiveMailbox = Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox>
   ```

   > [!IMPORTANT]
   > Önceki komutta, etkin olmayan posta kutusunu tanımlamak için **DistinguishedName** veya **ExchangeGUID** özelliğinin değerini kullanın. Bu özellikler kuruluşunuzdaki her posta kutusu için benzersizdir ancak etkin ve etkin olmayan bir posta kutusunun aynı birincil SMTP adresine sahip olması mümkündür.

2. Bu örnek, önceki komutta elde edilen özellikleri kullanır ve etkin olmayan posta kutusunu Ann Beebe kullanıcısı için etkin bir posta kutusuna kurtarır. *Name* ve *MicrosoftOnlineServicesID* parametreleri için belirtilen değerlerin kuruluşunuz içinde benzersiz olduğundan emin olun.

   ```powershell
   New-Mailbox -InactiveMailbox $InactiveMailbox.DistinguishedName -Name annbeebe -FirstName Ann -LastName Beebe -DisplayName "Ann Beebe" -MicrosoftOnlineServicesID Ann.Beebe@contoso.com -Password (ConvertTo-SecureString -String 'P@ssw0rd' -AsPlainText -Force) -ResetPasswordOnNextLogon $true
   ```

   Kurtarılan etkin olmayan posta kutusunun birincil SMTP adresi  *, MicrosoftOnlineServicesID*  parametresi tarafından belirtilen değerle aynı değere sahip olacaktır.

Etkin olmayan bir posta kutusunu kurtardıktan sonra yeni bir kullanıcı hesabı da oluşturulur. Lisans atayarak bu kullanıcı hesabını etkinleştirmeniz gerekir. Microsoft 365 yönetim merkezi lisans atamak için bkz. [Aynı anda kullanıcı ekleme ve lisans atama](../admin/add-users/add-users.md).

## <a name="more-information"></a>Daha fazla bilgi

- **Etkin olmayan posta kutusunu kurtarma ve geri yükleme arasındaki temel fark nedir?** Etkin olmayan bir posta kutusunu kurtardığınızda, posta kutusu yeni bir posta kutusuna dönüştürülür, etkin olmayan posta kutusunun içeriği ve klasör yapısı korunur ve posta kutusu yeni bir kullanıcı hesabına bağlanır. Kurtarıldıktan sonra, etkin olmayan posta kutusu artık yoktur ve yeni posta kutusunda içerikte yapılan değişiklikler, başlangıçta etkin olmayan posta kutusunda ayrı tutulmuş olan içeriği etkiler. Buna karşılık, etkin olmayan bir posta kutusunu geri yüklerken, içerik yalnızca başka bir posta kutusuna kopyalanır. Etkin olmayan posta kutusu korunur ve etkin olmayan bir posta kutusu olarak kalır. Hedef posta kutusunda içerikte yapılan değişiklikler, etkin olmayan posta kutusunda tutulan özgün içeriği etkilemez. Etkin olmayan posta kutusu hala In-Place eBulma kullanılarak aranabilir, içeriği başka bir posta kutusuna geri yüklenebilir veya daha sonraki bir tarihte kurtarılabilir veya silinebilir.

- **Etkin olmayan bir posta kutusunu kurtardığınızda ne olur?** Etkin olmayan bir posta kutusunu kurtardığınızda aşağıdaki işlemler gerçekleşir:

  - Etkin olmayan posta kutusuna uygulanan ayrı tutma, kurtarılmadan önce etkin olmayan posta kutusuna uygulanan ayrı tutma türüne göre değiştirilir veya kaldırılır.
    
    - **Koruma Kilidi ile bekletme ilkesini Microsoft 365.** Etkin olmayan posta kutusu [Koruma Kilidi](retention-preservation-lock.md) olan bir bekletme ilkesine dahil edildiyse, kurtarılan posta kutusu aynı bekletme ilkesine atanır.
    
    - **Koruma Kilidi olmadan bekletme ilkesini Microsoft 365.** Etkin olmayan posta kutusu Microsoft 365 bekletme ilkesinden kaldırılır. Ancak, belirli bir yaştan daha eski içeriği silen kuruluş genelinde saklama ilkeleri temelinde posta kutusu içeriğinin silinmesini önlemek için kurtarılan posta kutusunda Dava Tutma etkinleştirilir. Dava Bekletme'yi tutabilir veya kaldırabilirsiniz. Daha fazla bilgi için bkz. [Dava Tutma oluşturma](create-a-litigation-hold.md).

    - **Dava Beklemede.** Etkin olmayan posta kutusu için Dava Bekletme etkinleştirildiyse, kurtarılan posta kutusundan kaldırılır.

    - **Yerinde Saklama** In-Place Ayrı Tutma, kurtarılan posta kutusundan kaldırılır. Bu, kurtarılan posta kutusunun herhangi bir In-Place Ayrı Tutma'dan kaynak posta kutusu olarak kaldırıldığı veya eBulma aramasını In-Place anlamına gelir.

  - Tek öğe kurtarma süresi ( **RetainDeletedItemsFor** posta kutusu özelliği tarafından tanımlanır) 30 gün olarak ayarlanır. Genellikle, Exchange Online içinde yeni bir posta kutusu oluşturulduğunda, bu saklama süresi 14 gün olarak ayarlanır. Bunu en fazla 30 gün değerine ayarlamak, etkin olmayan posta kutusundan kalıcı olarak silinmiş (veya temizlenmiş) tüm verileri kurtarmak için daha fazla zaman sağlar. Ayrıca tek öğe kurtarmayı devre dışı bırakabilir veya tek öğe kurtarma süresini varsayılan 14 gün olarak ayarlayabilirsiniz. Daha fazla bilgi için bkz. [Posta kutusu için tek öğe kurtarmayı etkinleştirme veya devre dışı bırakma](/exchange/recipients-in-exchange-online/manage-user-mailboxes/enable-or-disable-single-item-recovery).

  - Bekletme saklama etkindir ve saklama süresi 30 gün olarak ayarlanır. Bu, varsayılan Exchange bekletme ilkesinin ve yeni posta kutusuna atanan kuruluş genelinde veya Exchange çapında Microsoft 365 bekletme ilkelerinin 30 gün boyunca işlenmeyeceği anlamına gelir. Bu, geri dönen çalışana veya kurtarılan etkin olmayan posta kutusunun yeni sahibine eski iletileri yönetme süresi verir. Aksi takdirde, Exchange veya Microsoft 365 bekletme ilkesi, Exchange veya Microsoft 365 bekletme ilkeleri için yapılandırılan ayarlara bağlı olarak süresi dolmuş eski posta kutusu öğelerini silebilir (veya öğeleri arşiv posta kutusuna taşıyabilir). 30 gün sonra bekletme saklama süresi dolar, **RetentionHoldEnabled** posta kutusu özelliği **False** olarak ayarlanır ve Yönetilen Klasör Yardımcısı posta kutusuna atanan ilkeleri işlemeye başlar. Bu ek süreye ihtiyacınız yoksa bekletme saklamayı kaldırabilirsiniz. Alternatif olarak, **Set-Mailbox -EndDateForRetentionHold** komutunu kullanarak bekletme saklama süresini artırabilirsiniz. Daha fazla bilgi için bkz [. Saklama bekletmeye posta kutusu yerleştirme](/exchange/security-and-compliance/messaging-records-management/mailbox-retention-hold).

- **Etkin olmayan posta kutusunun özgün durumunu korumanız gerekiyorsa kurtarılan posta kutusuna ayrı tutun.** Yeni posta kutusu sahibinin veya bekletme ilkesinin kurtarılan etkin olmayan posta kutusundan iletileri kalıcı olarak silmesini önlemek için, posta kutusunu Dava Tutma'ya yerleştirebilirsiniz. Daha fazla bilgi için bkz. [Dava Tutma oluşturma](./create-a-litigation-hold.md).

- **Etkin olmayan bir posta kutusunu kurtarırken hangi kullanıcı kimliğini kullanabilirsiniz?** Etkin olmayan bir posta kutusunu kurtardığınızda,  *MicrosoftOnlineServicesID*  parametresi için belirttiğiniz değer, etkin olmayan posta kutusuyla ilişkilendirilmiş özgün posta kutusundan farklı olabilir. Özgün kullanıcı kimliğini de kullanabilirsiniz. Ancak daha önce belirtildiği gibi, etkin olmayan posta kutusunu kurtardığınızda  *Name*  ve  *MicrosoftOnlineServicesID*  için kullanılan değerlerin kuruluşunuz içinde benzersiz olduğundan emin olun.

- **Etkin olmayan posta kutusunun posta kutusu saklama süresi dolmadıysa ne olur?** Etkin olmayan bir posta kutusu 30 günden kısa bir süre önce geçici olarak silinmişse, bu posta kutusunu kurtarmak için **New-Mailbox -InactiveMailbox** komutunu kullanamazsınız. İlgili kullanıcı hesabını geri yükleyerek kurtarmanız gerekir. Daha fazla bilgi için bkz. [Kuruluşunuzdan kullanıcı silme](../admin/add-users/delete-a-user.md).

- **Etkin olmayan bir posta kutusunun geçici olarak silinen posta kutusu saklama süresinin dolduğunu nasıl anlarsınız?** Aşağıdaki komutu çalıştırın:
    
  ```powershell
  Get-Mailbox -InactiveMailboxOnly <identity of inactive mailbox> | Format-List ExternalDirectoryObjectId
  ```
    
    - **ExternalDirectoryObjectId** özelliği için bir değer varsa, posta kutusu saklama süresi dolmuş demektir ve **New-Mailbox -InactiveMailbox** komutunu çalıştırarak etkin olmayan posta kutusunu kurtarabilirsiniz.
    - **ExternalDirectoryObjectId** özelliği için bir değer varsa, geçici olarak silinen posta kutusu saklama süresi dolmaz ve [kullanıcı hesabını geri yükleyerek](../admin/add-users/delete-a-user.md) posta kutusunu kurtarmanız gerekir.

- **Etkin olmayan bir posta kutusunu kurtardıktan sonra arşiv posta kutusunu etkinleştirmeyi göz önünde bulundurun.** Bu, geri dönen kullanıcının veya yeni çalışanın eski iletileri arşiv posta kutusuna taşımasına olanak tanır. Bekletme saklama süresi dolduğunda, Exchange Online posta kutularına atanan varsayılan Exchange MRM bekletme ilkesinin parçası olan arşiv ilkesi, iki yıl veya daha eski olan öğeleri arşiv posta kutusuna taşır. Arşiv posta kutusunu etkinleştirmezseniz, iki yıldan eski öğeler kullanıcının birincil posta kutusunda kalır. Daha fazla bilgi için bkz [. Arşiv posta kutularını etkinleştirme](enable-archive-mailboxes.md).
