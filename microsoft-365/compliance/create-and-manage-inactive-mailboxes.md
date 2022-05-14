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
description: silinen posta kutularının içeriğini Microsoft 365 koruyan etkin olmayan posta kutuları oluşturun ve yönetin.
ms.openlocfilehash: b7a33101135b43357b095af6864b54c618abd84d
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65417412"
---
# <a name="create-and-manage-inactive-mailboxes"></a>Etkin olmayan posta kutuları oluşturma ve yönetme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Etkin olmayan posta kutuları, kuruluşunuzdan ayrıldıktan sonra eski çalışanların e-postalarını tutmanıza olanak tanır ve uyumluluk veya yasal [nedenlerle eBulma izinleri](assign-ediscovery-permissions.md) verilmiş yetkili kişiler tarafından erişilebilir. Örneğin, yöneticiler, uyumluluk görevlileri ve kayıt yöneticileri, etkin olmayan posta kutusunun içeriğini aramak ve dışarı aktarmak için İçerik Arama'yı kullanabilir. Devre dışı bırakılmış posta kutuları e-posta alamaz ve kuruluşunuzun paylaşılan adres defterinde veya başka listelerinde görüntülenmez.

Etkin olmayan posta kutuları hakkında daha fazla bilgi için bkz. [Etkin olmayan posta kutuları hakkında bilgi edinin](inactive-mailboxes-in-office-365.md).

## <a name="create-an-inactive-mailbox"></a>Etkin olmayan posta kutusu oluşturma

Posta kutusunu devre dışı yapmak için posta kutusunda ayrı tutma ve ardından posta kutusunun veya ilgili kullanıcı hesabının silinmesi gerekir.

Posta kutusunun devre dışı bırakılabilmesi için, bir Exchange Online Plan 2 lisansına (veya Exchange Online Arşivleme eklenti lisansına sahip bir Exchange Online Plan 1 lisansına) atanması gerekir, böylece saklama işlemi silinmeden önce posta kutusuna uygulanabilir. Kullanıcı hesabı silindikten sonra, kullanıcı hesabıyla ilişkili tüm Exchange Online lisansları yeni bir kullanıcıya atanabilecektir.

Saklamayı posta kutusuna uygulamak için Microsoft 365 saklama kullanmanızı öneririz. Diğer yöntemler [, Etkin olmayan posta kutuları hakkında bilgi edinme bölümünde ele alınmıştır](inactive-mailboxes-in-office-365.md).

Posta kutusunu silmenin en iyi yolu<a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">, Microsoft 365 yönetim merkezi</a> ilgili kullanıcı hesabını silmektir. Kullanıcı hesaplarını silme hakkında bilgi için bkz. [Kuruluşunuzdan kullanıcı silme](../admin/add-users/delete-a-user.md). Ancak, Exchange Online PowerShell'de **Remove-Mailbox** cmdlet'ini kullanarak da posta kutusunu silebilirsiniz. Daha fazla bilgi için bkz. [Exchange Online'da kullanıcı posta kutularını silme veya geri yükleme](/exchange/recipients-in-exchange-online/delete-or-restore-mailboxes).

Aşağıdaki tabloda, farklı bekletme senaryoları için etkin olmayan posta kutusu oluşturma işlemi özetlenmiştir.

<br/>

|Hedef...|Bunu yapın...|Sonuç|
|---|---|---|
|Bir çalışan kuruluştan ayrıldıktan sonra posta kutusu içeriğini süresiz olarak saklama|1. Posta kutusu (bekletme ilkesi) veya belirli e-posta öğeleri (bir veya daha fazla bekletme etiketi) için saklama eylemleriyle Microsoft 365 bekletme ayarlarını uygulayın. <br /><br> 2. Bekletme ayarlarının uygulanmasını bekleyin. <br /><br> 3. Kullanıcının Microsoft 365 hesabını kaldırın.|Kurtarılabilir Öğeler klasöründeki öğeler de dahil olmak üzere bekletme ayarlarının uygulandığı etkin olmayan posta kutusunda bulunan tüm içerik süresiz olarak korunur.|
|Bir çalışan kuruluştan ayrıldıktan sonra tüm posta kutusu içeriğini belirli bir süre boyunca saklama ve ardından posta kutusunu silme|1. Saklama süresi dolduğunda öğeleri saklayan ve silecek bekletme ayarlarıyla posta kutusuna bir Microsoft 365 bekletme ilkesi uygulayın. <br /><br> 2. Bekletme ayarlarının uygulanmasını bekleyin. <br /><br> 3. Kullanıcının Microsoft 365 hesabını kaldırın.|Posta kutusu öğesinin saklama süresi dolduğunda, öğe Kurtarılabilir Öğeler klasörüne taşınır ve silinmiş öğe saklama süresi (Exchange posta kutuları için) sona erdiğinde etkin olmayan posta kutusundan kalıcı olarak silinir (temizlenir). Microsoft 365 bekletme ilkesinin bekletme süresi her zaman bir posta kutusu öğesinin alındığı veya oluşturulduğu özgün tarihe bağlıdır.|


> [!NOTE]
> İçeriği saklamak veya saklamak ve silmek üzere yapılandırılmış Microsoft 365 bekletme ayarları posta kutusuna veya posta kutusu öğelerine zaten uygulanmışsa ya da bir posta kutusuna dava tutma zaten yerleştirilmişse veya etkin olmayan posta kutusu oluşturmak için yapmanız gereken tek şey ilgili kullanıcı hesabını silmektir.


## <a name="view-a-list-of-inactive-mailboxes"></a>Etkin olmayan posta kutularının listesini görüntüleme

Kuruluşunuzdaki etkin olmayan posta kutularının listesini görüntülemek için:

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalı</a> gidin ve kuruluşunuzdaki bir Genel yönetici veya Uyumluluk yöneticisi hesabının kimlik bilgilerini kullanarak oturum açın.

2. Sol gezinti bölmesinde **Tümünü göster'i** ve ardından **Veri yaşam döngüsü yönetimiYenileştirme** >  **ilkeleri'ni** seçin.

3. **Etkin olmayan posta kutusu** seçeneğini belirleyin:

   ![Veri yaşam döngüsü yönetiminin Bekletme ilkeleri sayfasındaki Etkin Olmayan Posta Kutusu seçeneği.](../media/inactive-mailbox-option.png)

4. **Etkin olmayan posta kutuları sayfasında etkin** olmayan posta kutularının listesi görüntülenir. Etkin olmayan posta kutusuyla ilgili ayrıntıları görmek için birini seçin. Ayrıntılar, posta kutusunun Exchange tanımlayıcısını ve [Dava Tutma'da](create-a-litigation-hold.md) olup olmadığını içerir.
    
    Ayrıntılar bölmesinde Microsoft 365 bekletme ilkesi veya eBulma saklama gibi başka tür ayrı tutmalar görmezsiniz. Bu bilgileri bulmak için bkz. [Exchange Online posta kutusuna yerleştirilmiş saklama türünü tanımlama](identify-a-hold-on-an-exchange-online-mailbox.md).

Etkin olmayan çok sayıda posta kutunuz varsa, listede gördüğünüz ayrıntılar için csv dosyasında arama yapmak ve sıralamak daha kolay olabilir: **Etkin olmayan posta kutuları** sayfasında **Dışarı Aktar'ı** seçin:::image type="icon" source="../media/47205c65-babd-4b3a-bd7b-98dfd92883ba.png":::.

Alternatif olarak, etkin olmayan posta kutularının listesini görüntülemek için Exchange Online PowerShell'de aşağıdaki komutu çalıştırabilirsiniz:

```powershell
 Get-Mailbox -InactiveMailboxOnly | FT DisplayName,PrimarySMTPAddress,WhenSoftDeleted
```

Etkin olmayan posta kutularının ve diğer bilgilerin listesini csv dosyasına aktarmak için aşağıdaki komutu da çalıştırabilirsiniz. Bu örnekte CSV dosyası geçerli dizinde oluşturulur.

```powershell
Get-Mailbox -InactiveMailboxOnly | Select Displayname,PrimarySMTPAddress,DistinguishedName,ExchangeGuid,WhenSoftDeleted | Export-Csv InactiveMailboxes.csv -NoType
```

> [!NOTE]
> Etkin olmayan bir posta kutusunun SMTP adresi, etkin bir kullanıcı posta kutusuyla aynı olabilir. Bu durumda, etkin olmayan bir posta kutusunu benzersiz olarak tanımlamak için **DistinguishedName** veya **ExchangeGuid** özelliğinin değeri kullanılabilir.
  
## <a name="search-and-export-the-contents-of-an-inactive-mailbox"></a>Etkin olmayan posta kutusunun içeriğini arama ve dışarı aktarma

Microsoft Purview uyumluluk portalı İçerik Arama aracını kullanarak etkin olmayan posta kutusunun içeriğine erişebilirsiniz. Etkin olmayan bir posta kutusunda arama yaptığınızda, belirli öğeleri aramak için bir anahtar sözcük arama sorgusu oluşturabilir veya etkin olmayan posta kutusunun tüm içeriğini döndürebilirsiniz. Arama sonuçlarının önizlemesini görüntüleyebilir veya arama sonuçlarını bir Outlook Veri (PST) dosyasına veya tek tek e-posta iletileri olarak dışarı aktarabilirsiniz. Posta kutularını aramak ve arama sonuçlarını dışarı aktarmak için adım adım yordamlar için aşağıdaki konulara bakın:
  
- [İçerik arama](content-search.md)

- [Arama sonuçlarını dışarı aktarma](export-search-results.md)

Etkin olmayan posta kutularında arama yaparken göz önünde bulundurmak istediğiniz birkaç şey aşağıdadır.
  
- İçerik aramasında kullanıcı posta kutusu varsa ve bu posta kutusu devre dışı bırakılırsa, etkin olmayan posta kutusu etkin olmadığında aramayı yeniden çalıştırdığınızda içerik araması etkin olmayan posta kutusunda aramaya devam eder.

- Bazı durumlarda, kullanıcının etkin bir posta kutusu ve aynı SMTP adresine sahip etkin olmayan bir posta kutusu olabilir. Bu durumda, yalnızca içerik araması için konum olarak seçtiğiniz belirli posta kutusu aranacaktır. Başka bir deyişle, bir kullanıcının posta kutusunu aramaya eklerseniz, hem etkin hem de etkin olmayan posta kutularının aranacağını varsayamazsınız; yalnızca aramaya açıkça eklediğiniz posta kutusu aranacaktır.

- Aynı SMTP adresine sahip etkin bir posta kutusuna ve etkin olmayan posta kutusuna sahip olmaktan kaçınmanızı kesinlikle öneririz. Etkin olmayan posta kutusuna atanmış olan SMTP adresini yeniden kullanmanız gerekiyorsa, etkin olmayan posta kutusunu kurtarmanızı veya etkin olmayan posta kutusunun içeriğini etkin bir posta kutusuna (veya etkin posta kutusunun arşivine) geri yüklemenizi ve sonra etkin olmayan posta kutusunu silmenizi öneririz.

## <a name="change-the-hold-duration-for-an-inactive-mailbox"></a>Etkin olmayan posta kutusunun bekletme süresini değiştirme

Bir posta kutusu devre dışı bırakıldıktan sonra, etkin olmayan posta kutusuna uygulanan saklama süresini değiştirebilirsiniz.

Adım adım yordamlar için bkz. [Etkin olmayan posta kutusunun saklama süresini değiştirme](change-the-hold-duration-for-an-inactive-mailbox.md).
  
## <a name="recover-an-inactive-mailbox"></a>Etkin olmayan posta kutusunu kurtarma

Eski bir çalışan kuruluşunuza geri dönerse veya ayrılan çalışanın iş sorumluluklarını üstlenmesi için yeni bir çalışan işe alınırsa, etkin olmayan posta kutusunun içeriğini kurtarabilirsiniz. 

Etkin olmayan bir posta kutusunu kurtardığınızda, posta kutusu yeni bir posta kutusuna dönüştürülür, etkin olmayan posta kutusunun içeriği ve klasör yapısı korunur ve posta kutusu yeni bir kullanıcı hesabına bağlanır. Kurtarıldıktan sonra, etkin olmayan posta kutusu artık yok. 

Etkin olmayan bir posta kutusunu kurtardığınızda gerçekleşenler hakkında adım adım yordamlar ve daha fazla bilgi için bkz. [Etkin olmayan posta kutusunu kurtarma](recover-an-inactive-mailbox.md).
  
## <a name="restore-the-contents-of-an-inactive-mailbox-to-another-mailbox"></a>Etkin olmayan posta kutusunun içeriğini başka bir posta kutusuna geri yükleme

Başka bir çalışan eski bir çalışanın iş sorumluluklarını üstlenirse veya başka bir kişinin etkin olmayan posta kutusunun içeriğine erişmesi gerekiyorsa, etkin olmayan posta kutusunun içeriğini mevcut bir posta kutusuna geri yükleyebilir (veya birleştirebilirsiniz). 

Etkin olmayan bir posta kutusunu geri yüklerken, içerik başka bir posta kutusuna kopyalanır. Etkin olmayan posta kutusu korunur ve etkin olmayan bir posta kutusu olarak kalır. Etkin olmayan posta kutusu yine eBulma kullanılarak aranabilir, içeriği başka bir posta kutusuna geri yüklenebilir veya daha sonraki bir tarihte kurtarılabilir veya silinebilir. 

Adım adım yordamlar için bkz [. Etkin olmayan posta kutusunu geri yükleme](restore-an-inactive-mailbox.md).
  
## <a name="delete-an-inactive-mailbox"></a>Etkin olmayan posta kutusunu silme

Etkin olmayan posta kutusunun içeriğini artık saklamanız gerekmiyorsa, etkin olmayan posta kutusuna uygulanan saklamayı kaldırarak etkin olmayan posta kutusunu kalıcı olarak silebilirsiniz. Saklama veya saklama ilkesini kaldırdıktan sonra posta kutusu 183 gün boyunca saklanır ve bu süre boyunca kurtarılabilir. 183 gün sonra posta kutusu kalıcı silme için işaretlenir ve posta kutusu kurtarılamaz hale gelir. 

Etkin olmayan posta kutusunu kalıcı olarak silmek üzere saklama veya bekletme ilkesini kaldırmaya yönelik adım adım yordamlar için bkz [. Etkin olmayan posta kutusunu silme](delete-an-inactive-mailbox.md).
