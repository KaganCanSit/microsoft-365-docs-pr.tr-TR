---
title: Kullanıcı posta kutusunu paylaşılan posta kutusuna dönüştürme
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkEXCHANGE
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 2e122487-e1f5-4f26-ba41-5689249d93ba
description: 'Özel posta kutusunu, tek bir kişi yerine birkaç kişi tarafından erişilebilen bir paylaşılan posta kutusuna dönüştürmeyi öğrenin. '
ms.openlocfilehash: a1b82d744cc43f8119e9819537467133f2bae17c
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011965"
---
# <a name="convert-a-user-mailbox-to-a-shared-mailbox"></a>Kullanıcı posta kutusunu paylaşılan posta kutusuna dönüştürme

Kullanıcının posta kutusunu paylaşılan posta kutusuna dönüştürürken, var olan tüm e-posta ve takvim korunur. Yalnızca şu anda paylaşılan posta kutusunda, bir kişi yerine birkaç kişi bu posta kutusuna erişebilirsiniz. Daha sonraki bir tarihte, paylaşılan posta kutusunu yeniden kullanıcı (özel) posta kutusuna dönüştürebilirsiniz.

> [!TIP]
> Bu konudaki adımlarda yardıma ihtiyacınız varsa, [Microsoft küçük işletme uzmanıyla çalışmayı göz önünde bulundurabilirsiniz](https://go.microsoft.com/fwlink/?linkid=2186871). İş Yardımı ile, işe alımtan günlük kullanıma kadar işlerinizi büyüttükçe siz ve çalışanlarınız küçük işletme uzmanlarına 24 saat erişim elde ediyor.

## <a name="before-you-begin"></a>Başlamadan önce

**İşte, gerçekten de ihtiyacınız olan bazı önemli şeyler:**

- Dönüştüren kullanıcı posta kutusunu paylaşılan posta kutusuna dönüştürmeden önce bu posta kutusuna atanmış bir lisans olması gerekir. Aksi takdirde, posta kutusunu dönüştürme seçeneğini görmeyebilirsiniz. Lisansı kaldırdınız, posta kutusunu dönüştürebilirsiniz. Posta kutusunu paylaşılan posta kutusuna dönüştürdikten sonra, kullanıcının hesabından lisansı kaldırabilirsiniz.

- Paylaşılan posta kutularına lisans atanmadan en çok 50 GB veri olabilir. Daha fazla veri tutmak için bu lisansa atanmış bir lisansa ihtiyacınız var. Lisansı kaldırmak için, paylaşılan posta kutusundan çok sayıda büyük e-postayı (ekleri olan e-postaları) silmeniz gerekiyor olabilir.

- Eski kullanıcının hesabını silmeyin. Bu, paylaşılan posta kutusunun tutturucusu için gereklidir. Kullanıcı hesabını zaten sildikten sonra, bkz [Silinen kullanıcının posta kutusunu dönüştürme](#convert-the-mailbox-of-a-deleted-user).

- Posta kutusu paylaşılan posta kutusuna dönüştürüldikten sonra kurallar korunur.

## <a name="use-the-classic-exchange-admin-center-to-convert-a-mailbox"></a>Posta kutusunu dönüştürmek Exchange Klasik Posta Kutusu yönetim merkezini kullanma
 
1. Klasik Grup <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">yönetim Exchange gidin</a>.

2. Alıcılar **Posta Kutuları'ı** \> **seçin**.

3. Kullanıcı posta kutusunu seçin. Paylaşılan **Posta Kutusuna Dönüştür'in altında** Dönüştür'e **seçin**.

4. Posta kutusu 50 GB'tan küçükse kullanıcının [lisansını](../manage/remove-licenses-from-users.md) kaldırabilir ve ödemeyi durdurabilirsiniz. Kullanıcının hesabını silmeyin. Paylaşılan posta kutusunun bir bağlayıcı olarak orada olması gerekir. Kuruluşdan ayrılmakta olan bir çalışanın posta kutusunu dönüştürerek, artık oturum açamay olduğundan emin olmak için ek adımlar atabilirsiniz. Daha fazla bilgi için bkz[. Eski bir çalışanı iş Microsoft 365](../add-users/remove-former-employee.md).
    
> [!NOTE]
> Posta kutusu dönüştürme sırasında kullanıcının parolasını sıfırlamak gerekmez. Ancak parola sıfırlanmazsa, posta **kutusu dönüştürmesi tamamlanır** ve özgün kullanıcı adı ve parola çalışmaya devam eder.

Paylaşılan posta kutuları hakkında ihtiyacınız olan diğer her şey için bkz. Paylaşılan [posta kutuları hakkında ve](about-shared-mailboxes.md) [Paylaşılan posta kutusu oluşturma](create-a-shared-mailbox.md).

> [!NOTE]
> Paylaşılan posta kutuları için ayrı bir lisans gerekli değil. Bununla birlikte, paylaşılan bir posta kutusuna In-Place Arşivle'yi etkinleştirmek veya In-Place'i Tutma ya da Mahkeme Exchange Online Planı 1'i etkinleştirmek için posta kutusuna Exchange Online Arşivleme veya Exchange Online Plan 2 lisansı atamanız gerekir.

## <a name="use-the-new-exchange-admin-center-to-convert-a-mailbox"></a>Posta kutusunu dönüştürmek Exchange Posta Kutusu yönetim merkezini kullanma

1. <a href="https://admin.exchange.microsoft.com/#/homepage" target="_blank"> Exchange yönetim merkezine gidin</a>.

2. Alıcılar **Posta Kutuları'ı** \> **seçin**.

3. Kullanıcı posta kutusunu seçin. Posta Kutusu **sekmesindeki** Diğer **Eylemler'in altında** Paylaşılan posta **kutusuna dönüştür'e tıklayın**.

4. Posta kutusu 50 GB'tan küçükse kullanıcının [lisansını](../manage/remove-licenses-from-users.md) kaldırabilir ve ödemeyi durdurabilirsiniz. Kullanıcının hesabını silmeyin. Paylaşılan posta kutusunun bir bağlayıcı olarak orada olması gerekir. Kuruluşdan ayrılmakta olan bir çalışanın posta kutusunu dönüştürerek, artık oturum açamayacaklarını emin olmak için ek adımlar atabilirsiniz. Lütfen Bkz[. Eski bir çalışanı iş Microsoft 365](../add-users/remove-former-employee.md).
    
> [!NOTE]
> Posta kutusu dönüştürme sırasında kullanıcının parolasını sıfırlamak gerekmez. Ancak parola sıfırlanmazsa, posta **kutusu dönüştürmesi tamamlanır** ve özgün kullanıcı adı ve parola çalışmaya devam eder.

Paylaşılan posta kutuları hakkında ihtiyacınız olan diğer her şey için bkz. Paylaşılan [posta kutuları hakkında ve](about-shared-mailboxes.md) [Paylaşılan posta kutusu oluşturma](create-a-shared-mailbox.md).

> [!NOTE]
> Paylaşılan posta kutuları için ayrı bir lisans gerekli değil. Bununla birlikte, paylaşılan bir posta kutusuna In-Place Arşivle'yi etkinleştirmek veya In-Place'i Tutma ya da Mahkeme Exchange Online Planı 1'i etkinleştirmek için posta kutusuna Exchange Online Arşivleme veya Exchange Online Plan 2 lisansı atamanız gerekir.

## <a name="convert-the-mailbox-of-a-deleted-user"></a>Silinmiş kullanıcının posta kutusunu dönüştürme

Kullanıcı hesabını sildikten sonra, eski posta kutularını bir paylaşım posta kutusuna dönüştürmek için şu adımları izleyin:

1. [Kullanıcının hesabını geri yükleme](../add-users/restore-user.md).

2. Kullanıcı lisansının Microsoft 365 emin olun.

3. Kullanıcının parolasını sıfırlayın.
    
4. Posta kutusunun yeniden oluşturul olması için 20-30 dakika bekleyin.
      
6. Posta kutusu yeniden oluşturulduktan sonra, kullanıcının posta kutusundan lisansı kaldırın. Kullanıcının eski posta kutusunu silmeyin. Paylaşılan posta kutusunun bir bağlayıcı olarak orada olması gerekir.
    
7. Paylaşılan posta kutusuna üye ekleyin.

## <a name="convert-a-shared-mailbox-back-to-a-users-private-mailbox"></a>Paylaşılan posta kutusunu kullanıcının (özel) posta kutusuna geri dönüştürme

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezine</a> gidin.
   
2. Paylaşılan **Alıcılar'ı** \> **seçin**.

3. Paylaşılan posta kutusunu seçin. Normal **Posta Kutusuna Dönüştür'in altında** Dönüştür'e **seçin**.

4. Yönetim merkezine geri dönme. **Kullanıcılar'ın** altında, eski paylaşılan posta kutusuyla ilişkilendirilmiş kullanıcı hesabını seçin. Hesaba lisans atlayın ve sonra parolayı sıfırlayın.

   Posta kutusunun ayarlaması birkaç dakika sürer, ancak bundan sonra, o hesabı kullanacak olan kişi kullanıma hazır olur. Oturum a açmaları, daha önce paylaşılan posta kutusunda yer alan e-posta ve takvim öğelerini görmelerini sağlar.

## <a name="convert-a-users-mailbox-in-a-hybrid-environment"></a>Karma ortamda kullanıcının posta kutusunu dönüştürme

Karma ortamda kullanıcı posta kutusunu paylaşılan posta kutusuna dönüştürme hakkında daha fazla bilgi Exchange bkz:

 - [Şirket içi posta kutusunda uzak paylaşılan posta kutusu oluşturmak veya değiştirmek için cmdlet'ler Exchange.](https://support.microsoft.com/office/cmdlets-to-create-or-modify-a-remote-shared-mailbox-in-an-on-premises-exchange-environment-9e83fb59-c001-729c-a4c0-b2964c154b49)
 - [Dizin eşitlemesi karma bir dağıtımda çalıştırıldıktan sonra, paylaşılan posta kutuları beklenmedik bir Exchange kutularına dönüştürülür](/exchange/troubleshoot/user-and-shared-mailboxes/shared-mailboxes-unexpectedly-converted-to-user-mailboxes)
 

> [!NOTE]
> Kuruluş Yönetimi veya Alıcı Yönetimi rol grubunun üyesiyseniz, kullanıcı posta kutusunu şirket içi paylaşılan posta kutusuna değiştirmek için Exchange Yönetim Kabuğu'nda kullanabilirsiniz. Örneğin, `Set-Mailbox -Identity mailbox1@contoso.com -Type Shared`.

## <a name="related-content"></a>İlgili içerik

[Paylaşılan posta kutuları hakkında](about-shared-mailboxes.md) (makale)\
[Paylaşılan posta kutusu oluşturma](create-a-shared-mailbox.md) (makale)\
[Paylaşılan posta kutusunu yapılandırma](configure-a-shared-mailbox.md) (makale)\
[Paylaşılan posta kutusundan lisans kaldırma](remove-license-from-shared-mailbox.md) (makale)\
[Paylaşılan posta kutularıyla ilgili sorunları çözme](resolve-issues-with-shared-mailboxes.md) (makale)
