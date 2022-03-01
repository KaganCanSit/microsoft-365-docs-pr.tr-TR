---
title: Etkin olmayan posta kutuları oluşturma ve yönetme
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 296a02bd-ebde-4022-900e-547acf38ddd7
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
description: Aynı dosyada silinmiş posta kutularının içeriğinin korunarak etkin olmayan posta kutularını Microsoft 365.
ms.openlocfilehash: 18bcc4c69fc15ea44253bbc4b0f5d5813cc23085
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010881"
---
# <a name="create-and-manage-inactive-mailboxes"></a>Etkin olmayan posta kutuları oluşturma ve yönetme

Etkin olmayan posta kutuları, kuruluşdan ayrıldıktan sonra eski çalışanların e-postalarını tutmanıza izin veriyor ve uyumluluk veya yasal nedenlerle [eBulma](assign-ediscovery-permissions.md) izinleri verilmiş olan yetkili kişiler tarafından erişilebilir. Örneğin yöneticiler, uyumluluk yetkililerini ve kayıt yöneticilerini, etkin olmayan bir posta kutusunun içeriğini aramak ve dışarı aktararak İçerik Arama'ya aktarabilirsiniz. Devre dışı bırakılmış posta kutuları e-posta alamaz ve kuruluşunuzun paylaşılan adres defterinde veya başka listelerinde görüntülenmez.

Etkin olmayan posta kutuları hakkında daha fazla bilgi için bkz[. Etkin olmayan posta kutuları hakkında bilgi.](inactive-mailboxes-in-office-365.md)

## <a name="create-an-inactive-mailbox"></a>Etkin olmayan posta kutusu oluşturma

Posta kutusunu devre dışı yapmak için, posta kutusunun üzerinde bekleyin ve sonra posta kutusunu veya buna karşılık gelen kullanıcı hesabını silin.

Posta kutusunu devre dışı tutmak için, posta kutusunun silinmesi için posta kutusuna bir tutmanın uygulanamadan önce ona Exchange Online Plan 2 lisansı (veya Exchange Online Arşivleme eklenti lisansı olan bir Exchange Online Plan 1 lisansı) atanmalıdır. Kullanıcı hesabı silindikten sonra, Exchange Online hesabıyla ilişkilendirilmiş tüm lisanslar yeni bir kullanıcıya atanacak.

Saklamayı posta Microsoft 365 için bekletmeyi bu saklamayı kullanmanızı öneririz. Diğer yöntemler, Etkin olmayan posta kutuları [hakkında bilgi sahibi olun konusunda ele alın almaktadır](inactive-mailboxes-in-office-365.md).

Posta kutusunu silmenin en iyi yolu, posta kutusunda ilgili kullanıcı hesabını <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">silmek Microsoft 365 yönetim merkezi</a>. Kullanıcı hesaplarını silme hakkında bilgi için bkz. [Kuruluştan kullanıcı silme](../admin/add-users/delete-a-user.md). Bununla birlikte, powershell'de **Remove-Mailbox** cmdlet'ini kullanarak da Exchange Online silebilirsiniz. Daha fazla bilgi için bkz[. Posta kutularında kullanıcı posta kutularını silme Exchange Online](/exchange/recipients-in-exchange-online/delete-or-restore-mailboxes).

Aşağıdaki tabloda, farklı bekletme senaryoları için etkin olmayan bir posta kutusu yapma işlemi özetlenmiştir.

<br/>

|Hedef...|Bunu yap...|Sonuç|
|---|---|---|
|Çalışan kuruluştan ayrıldığında posta kutusu içeriğini süresiz olarak koruma|1. Posta Microsoft 365 veya belirli e-posta öğelerine (bir veya birden çok bekletme etiketi) yönelik bekletme eylemlerini kullanarak bekletme ayarlarını kullanın. <br /><br> 2. Bekletme ayarlarının uygulanması için bekleyin. <br /><br> 3. Kullanıcının hesabı Microsoft 365 kaldırın.|Kurtarılabilir Öğeler klasöründeki öğeler de dahil olmak üzere, bekletme ayarlarının uygulandığı etkin olmayan posta kutusunun tüm içeriği süresiz olarak korunur.|
|Çalışan kuruluştan ayrıldığında belirli bir süre için tüm posta kutusu içeriğini tutma ve sonra posta kutusunu silme|1. Bekletme Microsoft 365 sona erdiğinde öğeleri alıkoyan ve silen bekletme ayarları olan posta kutusuna bir bekletme ilkesi uygulayabilirsiniz. <br /><br> 2. Bekletme ayarlarının uygulanması için bekleyin. <br /><br> 3. Kullanıcının hesabı Microsoft 365 kaldırın.|Posta kutusu öğesinin bekletme süresi dolduğunda, öğe Kurtarılabilir Öğeler klasörüne taşınır ve ardından silinmiş öğe bekletme süresi (Exchange posta kutuları için) sona erdiğinde etkin olmayan posta kutusundan kalıcı olarak silinir (temizlenebilir). Bekletme ilkesine bağlı Microsoft 365, her zaman posta kutusu öğesinin ilk teslim tarihine veya oluşturulma tarihine dayalıdır.|


> [!NOTE]
> İçeriği Microsoft 365 veya alıkoyma ve silmeyi yapılandırmış olan bekletme ayarları zaten posta kutusu veya posta kutusu öğelerine uygulanmışsa veya bir posta kutusuna Mahkeme tutma zaten yerleştirilmişse veya etkin olmayan bir posta kutusu oluşturmak için tek gereken ilgili kullanıcı hesabını silmektir.


## <a name="view-a-list-of-inactive-mailboxes"></a>Etkin olmayan posta kutularının listesini görüntüleme

Kurumda etkin olmayan posta kutularının listesini görüntülemek için:

1. Genel <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">yönetici Microsoft 365 uyumluluk merkezi</a> veya kuruluşta Uyumluluk yöneticisi hesabının kimlik bilgilerini kullanarak oturum açın.

2. Sol gezinti bölmesinde, Her şeyi **göster'e tıklayın** ve sonra da **Bilgi idaresiRetention'a** >  **tıklayın**.

   ![Bekletme sayfasında Etkin Olmayan Posta Kutusu düğmesine tıklayın.](../media/MCCInactiveMailboxes1.png)

3. Bekletme sayfasında **,** etkin olmayan posta **kutularının listesini** görüntülemek için Etkin Değil posta kutusu'ne tıklayın.

4. Etkin olmayan posta kutusu hakkında bilgilerin olduğu bir çıkış sayfası görüntülemek için etkin olmayan bir posta kutusu seçin.

   ![Uçarak çıkış sayfasında etkin olmayan posta kutusuyla ilgili ayrıntılar görüntülenir.](../media/MCCInactiveMailboxes2.png)  

Arama sonuçlarını dışarı ![aktar simgesine tıkabilirsiniz.](../media/47205c65-babd-4b3a-bd7b-98dfd92883ba.png) **Dışarı** aktararak, kurumda etkin olmayan posta kutuları hakkında ek bilgiler içeren bir CSV dosyası indirebilirsiniz.

Alternatif olarak, etkin olmayan posta kutularının listesini görüntülemek Exchange Online PowerShell'de aşağıdaki komutu çalıştırabilirsiniz.

```powershell
 Get-Mailbox -InactiveMailboxOnly | FT DisplayName,PrimarySMTPAddress,WhenSoftDeleted
```

Etkin olmayan posta kutularının listesini ve diğer bilgileri bir CSV dosyasına dışarı aktarmak için aşağıdaki komutu da çalıştırabilirsiniz. Bu örnekte, CSV dosyası geçerli dizinde oluşturulur.

```powershell
Get-Mailbox -InactiveMailboxOnly | Select Displayname,PrimarySMTPAddress,DistinguishedName,ExchangeGuid,WhenSoftDeleted | Export-Csv InactiveMailboxes.csv -NoType
```

> [!NOTE]
> Etkin olmayan bir posta kutusunun etkin kullanıcı posta kutusuyla aynı SMTP adresine sahip olması mümkündür. Bu durumda, etkin olmayan bir posta kutusunu benzersiz olarak tanımlamak için **DistinguishedName** veya **ExchangeGuid** özelliğinin değeri kullanılabilir.
  
## <a name="search-and-export-the-contents-of-an-inactive-mailbox"></a>Etkin olmayan posta kutusunun içeriğini arama ve dışarı aktarma

Etkin olmayan posta kutusunun içeriğine erişmek için, arama sonuçlarında İçerik Arama aracını Microsoft 365 uyumluluk merkezi. Etkin olmayan bir posta kutusunda arama yapmak için bir anahtar sözcük arama sorgusu oluşturabilir veya etkin olmayan posta kutusunun içeriğinin tamamını geri getirebilirsiniz. Arama sonuçlarını önizler veya arama sonuçlarını bir Outlook Veri (PST) dosyasına veya tek tek e-posta iletileri olarak dışarı aktarabilirsiniz. Posta kutularını arama ve arama sonuçlarını dışarı aktarma işlemleri için adım adım yordamlar için, aşağıdaki konulara bakın:
  
- [İçerik arama](content-search.md)

- [Arama sonuçlarını dışarı aktarma](export-search-results.md)

Etkin olmayan posta kutularında arama ararken gözlerde tutmanız gereken birkaç şey vardır.
  
- İçerik aramada bir kullanıcı posta kutusu varsa ve bu posta kutusu etkin değil olarak yapılıyorsa, içerik araması etkin olmayan posta kutusuna geldiğinde arama özelliği etkin olmayan posta kutusunda arama yapmaya devam eder.

- Bazı durumlarda, kullanıcının etkin bir posta kutusu ve aynı SMTP adresine sahip etkin olmayan bir posta kutusu olabilir. Bu durumda, yalnızca içerik arama konumu olarak belirli posta kutusunda arama yalnızca sizin seçmeniz gerekir. Başka bir deyişle, aramaya bir kullanıcının posta kutusunu eklersiniz, hem etkin hem de etkin olmayan posta kutularında arama olacağını varsaymayabilirsiniz; yalnızca aramaya açıkça eklemek istediğiniz posta kutusunda arama yapmak gerekir.

- Etkin bir posta kutusuna ve aynı SMTP adresine sahip etkin olmayan posta kutularına sahip olmaktan kaçınmanızı kesinlikle öneririz. Etkin olmayan bir posta kutusuna atanmış olan SMTP adresini yeniden kullanmanız gerekirse, etkin olmayan posta kutusunu kurtarmanızı veya etkin olmayan posta kutusunun içeriğini etkin bir posta kutusuna (veya etkin bir posta kutusunun arşivini) geri yüklemenizi ve sonra etkin olmayan posta kutusunu silmenizi öneririz.

## <a name="change-the-hold-duration-for-an-inactive-mailbox"></a>Etkin olmayan posta kutusunun tutma süresini değiştirme

Posta kutusu devre dışı yapıldıktan sonra, etkin olmayan posta kutusuna uygulanan tutma süresini değiştirebilirsiniz.

Adım adım yordamlar için bkz. [Etkin olmayan bir posta kutusunun tutma süresini değiştirme](change-the-hold-duration-for-an-inactive-mailbox.md).
  
## <a name="recover-an-inactive-mailbox"></a>Etkin olmayan posta kutusunu kurtarma

Eski bir çalışan organizasyona dönerse veya yeni bir çalışan işe alınarak ayrılan çalışanın iş sorumluluklarını almaya işe alındısa, etkin olmayan posta kutusunun içeriğini kurtarabilirsiniz. 

Etkin olmayan bir posta kutusunu kurtarsanız, posta kutusu yeni bir posta kutusuna dönüştürülür, etkin olmayan posta kutusunun içeriği ve klasör yapısı korunur ve posta kutusu yeni bir kullanıcı hesabına bağlıdır. Kurtarılan etkin olmayan posta kutusu artık yoktur. 

Etkin olmayan bir posta kutusunu kurtararak ilgili adım adım yordamlar ve daha fazla bilgi için bkz. Etkin olmayan [posta kutusunu kurtarma](recover-an-inactive-mailbox.md).
  
## <a name="restore-the-contents-of-an-inactive-mailbox-to-another-mailbox"></a>Etkin olmayan posta kutusunun içeriğini başka bir posta kutusuna geri yükleme

Başka bir çalışan eski bir çalışanın iş sorumluluklarını alırsa veya başka bir kişi etkin olmayan posta kutusunun içeriğine erişmesi gerekirse, etkin olmayan posta kutusunun içeriğini mevcut bir posta kutusuna geri yükleyebilir (veya birleştirebilirsiniz). 

Etkin olmayan bir posta kutusunu geri yüklemek, içerikler başka bir posta kutusuna kopyalanır. Etkin olmayan posta kutusu korunur ve etkin olmayan posta kutusu olarak kalır. Etkin olmayan posta kutusunda eKbulma kullanılarak da arama kullanılabilir, içeriği başka bir posta kutusuna geri yüklenebilir veya daha sonraki bir tarihte kurtarılabilir veya silinebilir. 

Adım adım yordamlar için bkz. Etkin olmayan [posta kutusunu geri yükleme](restore-an-inactive-mailbox.md).
  
## <a name="delete-an-inactive-mailbox"></a>Etkin olmayan posta kutusunu silme

Artık etkin olmayan posta kutusunun içeriğini tutmanız gerekmeyecekse, etkin olmayan posta kutusuna uygulanan tutmayı kaldırarak etkin olmayan posta kutusunu kalıcı olarak silebilirsiniz. Saklama veya bekletme ilkesi kaldırılan posta kutusu 183 gün boyunca korunur ve bu süre boyunca kurtarılabilir. 183 gün sonra, posta kutusu kalıcı olarak silinmek üzere işaretlenir ve posta kutusu kurtarılamaz hale gelir. 

Etkin olmayan bir posta kutusunu kalıcı olarak silmek için bekletmeyi veya bekletme ilkesi kaldırmaya yönelik adım adım yordamlar için bkz. Etkin olmayan posta [kutusunu silme](delete-an-inactive-mailbox.md).
