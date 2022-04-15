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
description: 'Özel posta kutusunu yalnızca bir kişi yerine birkaç kişi tarafından erişilebilen paylaşılan posta kutusuna dönüştürmeyi öğrenin. '
ms.openlocfilehash: 4838dc7bd4856c89448cb501fdd20066d1c97aa2
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2022
ms.locfileid: "64861950"
---
# <a name="convert-a-user-mailbox-to-a-shared-mailbox"></a>Kullanıcı posta kutusunu paylaşılan posta kutusuna dönüştürme

Kullanıcının posta kutusunu paylaşılan posta kutusuna dönüştürdüğünüzde, var olan tüm e-posta ve takvim korunur. Yalnızca şimdi paylaşılan posta kutusunda bir kişi yerine birkaç kişinin erişebileceği bir posta kutusu var. Daha sonraki bir tarihte, paylaşılan posta kutusunu bir kullanıcı (özel) posta kutusuna geri dönüştürebilirsiniz.

> [!TIP]
> Bu konuda verilen adımlarla ilgili yardıma ihtiyacınız varsa, [bir Microsoft küçük işletme uzmanıyla çalışmayı](https://go.microsoft.com/fwlink/?linkid=2186871) göz önünde bulundurun. İşletme Yardımı ile, işletmenizi büyütürken katılımdan gündelik kullanıma kadar her aşamada siz ve çalışanlarınız günün 24 saati küçük işletme uzmanlarına erişebilirsiniz.

## <a name="before-you-begin"></a>Başlamadan önce

**Bilmeniz gereken bazı önemli şeyler şunlardır**:

- Kullanıcı posta kutusunu paylaşılan posta kutusuna dönüştürmeden önce kullanıcı posta kutusuna bir lisans atanması gerekir. Aksi takdirde, posta kutusunu dönüştürme seçeneğini görmezsiniz. Lisansı kaldırdıysanız, posta kutusunu dönüştürebilmeniz için lisansı geri ekleyin. Kullanıcı posta kutusunu paylaşılan posta kutusuna dönüştürdükten sonra, kullanıcının hesabından lisansı kaldırabilirsiniz.

- Lisans olmadan paylaşılan posta kutuları 50 GB ile sınırlıdır. Lisansı kaldırabilmek için paylaşılan posta kutusundan bir dizi büyük iletiyi (ekleri olan iletiler) silmeniz gerekebilir.

  Boyut sınırını 100 GB'a yükseltmek için paylaşılan posta kutusuna bir Exchange Online Plan 2 lisansı atayın.

  Paylaşılan posta kutusuna bir Exchange Online Plan 1 lisansı ve Exchange Online Arşivleme eklenti lisansı atarsanız, ek arşiv depolama kapasitesi için otomatik genişletme arşivlemeyi etkinleştirebilirsiniz.

- Paylaşılan posta kutusunu tutturmak için hesap gerektiğinden eski kullanıcının hesabını silmeyin. Kullanıcı hesabını zaten sildiyseniz, bkz [. Silinen kullanıcının posta kutusunu dönüştürme](#convert-the-mailbox-of-a-deleted-user).

- Kullanıcı posta kutusunun hesap parolasını sıfırlamanız gerekmez. Ancak, parolayı sıfırlamazsanız, dönüştürme tamamlandıktan sonra **özgün kullanıcı adı ve parola paylaşılan posta kutusunda çalışmaya devam eder** .

- Kullanıcı posta kutusu paylaşılan posta kutusuna dönüştürüldükten sonra gelen kutusu kuralları korunur.

- Paylaşılan posta kutusuna In-Place Ayrı Tutma veya Dava Ayrı Tutması uygulamak için, paylaşılan posta kutusuna Exchange Online Plan 2 lisansı *veya* Exchange Online Plan 1 lisansı ve Exchange Online Arşivleme eklenti lisansı atamanız gerekir.

## <a name="use-the-classic-exchange-admin-center-to-convert-a-mailbox"></a>Bir posta kutusunu dönüştürmek için Klasik Exchange yönetim merkezini kullanma

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Klasik Exchange yönetim merkezine</a> gidin.

2. Alıcılar **Posta Kutuları'nı** \> seçin.

3. Kullanıcı posta kutusunu seçin. **Paylaşılan Posta Kutusuna Dönüştür** altında **Dönüştür'ü** seçin.

4. Posta kutusu 50 GB'tan küçükse, [kullanıcıdan lisansı](../manage/remove-licenses-from-users.md) kaldırabilir ve bunun için ödeme yapmayı durdurabilirsiniz. Kullanıcının hesabını silmeyin. Paylaşılan posta kutusunun yer işareti olarak orada olması gerekir. Kuruluşunuzdan ayrılan bir çalışanın posta kutusunu dönüştürüyorsanız, artık oturum açamayacaklarından emin olmak için ek adımlar uygulamanız gerekir. Daha fazla bilgi için bkz. [Eski çalışanı Microsoft 365 kaldırma](../add-users/remove-former-employee.md).

Paylaşılan posta kutuları hakkında bilmeniz gereken diğer her şey için bkz. [Paylaşılan posta kutuları hakkında](about-shared-mailboxes.md) ve [Paylaşılan posta kutusu oluşturma](create-a-shared-mailbox.md).

## <a name="use-the-new-exchange-admin-center-to-convert-a-mailbox"></a>Posta kutusunu dönüştürmek için Yeni Exchange yönetim merkezini kullanma

1. <a href="https://admin.exchange.microsoft.com/#/homepage" target="_blank"> Exchange yönetim merkezine</a> gidin.

2. Alıcılar **Posta Kutuları'nı** \> seçin.

3. Kullanıcı posta kutusunu seçin. **Posta Kutusu** sekmesindeki **Diğer Eylemler'in** altında **Paylaşılan posta kutusuna dönüştür'ü** seçin.

4. Posta kutusu 50 GB'tan küçükse, [kullanıcıdan lisansı](../manage/remove-licenses-from-users.md) kaldırabilir ve bunun için ödeme yapmayı durdurabilirsiniz. Kullanıcının hesabını silmeyin. Paylaşılan posta kutusunun yer işareti olarak orada olması gerekir. Kuruluşunuzdan ayrılan bir çalışanın posta kutusunu dönüştürüyorsanız, artık oturum açamayacağından emin olmak için ek adımlar uygulamanız gerekir. Lütfen bkz. [Eski çalışanı Microsoft 365 kaldırma](../add-users/remove-former-employee.md).

Paylaşılan posta kutuları hakkında bilmeniz gereken diğer her şey için bkz. [Paylaşılan posta kutuları hakkında](about-shared-mailboxes.md) ve [Paylaşılan posta kutusu oluşturma](create-a-shared-mailbox.md).

## <a name="convert-the-mailbox-of-a-deleted-user"></a>Silinen kullanıcının posta kutusunu dönüştürme

Kullanıcı hesabını sildikten sonra, eski posta kutularını paylaşım posta kutusuna dönüştürmek için şu adımları izleyin:

1. [Kullanıcının hesabını geri yükleyin](../add-users/restore-user.md).

2. Microsoft 365 lisansının atandığından emin olun.

3. Kullanıcının parolasını sıfırlayın.

4. Posta kutularının yeniden oluşturulması için 20-30 dakika bekleyin.

5. Posta kutusu yeniden oluşturulduktan sonra kullanıcının posta kutusundan lisansı kaldırın. Kullanıcının eski posta kutusunu silmeyin. Paylaşılan posta kutusunun yer işareti olarak orada olması gerekir.

6. Paylaşılan posta kutusuna üye ekleyin.

## <a name="convert-a-shared-mailbox-back-to-a-users-private-mailbox"></a>Paylaşılan posta kutusunu kullanıcının (özel) posta kutusuna geri dönüştürme

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezine</a> gidin.

2. **Paylaşılan** **Alıcılar'ı** \> seçin.

3. Paylaşılan posta kutusunu seçin. **Normal Posta Kutusuna Dönüştür** altında **Dönüştür'ü** seçin.

4. yönetim merkezine Geri dön. **Kullanıcılar'ın** altında, eski paylaşılan posta kutusuyla ilişkili kullanıcı hesabını seçin. Hesaba bir lisans atayın ve ardından parolayı sıfırlayın.

   Posta kutusunun ayarlanması birkaç dakika sürer, ancak bundan sonra bu hesabı kullanacak olan kişi hazır olur. Oturum açtıklarında, paylaşılan posta kutusunda kullanılan e-posta ve takvim öğelerini görürler.

## <a name="convert-a-users-mailbox-in-a-hybrid-environment"></a>Karma ortamda kullanıcının posta kutusunu dönüştürme

Exchange Karma ortamında kullanıcı posta kutusunu paylaşılan posta kutusuna dönüştürme hakkında daha fazla bilgi için bkz:

- [Şirket içi Exchange ortamında uzak paylaşılan posta kutusu oluşturmak veya değiştirmek için cmdlet'ler](https://support.microsoft.com/office/cmdlets-to-create-or-modify-a-remote-shared-mailbox-in-an-on-premises-exchange-environment-9e83fb59-c001-729c-a4c0-b2964c154b49)
- [Dizin eşitlemesi Exchange karma dağıtımda çalıştırıldıktan sonra paylaşılan posta kutuları beklenmedik şekilde kullanıcı posta kutularına dönüştürülür](/exchange/troubleshoot/user-and-shared-mailboxes/shared-mailboxes-unexpectedly-converted-to-user-mailboxes)

> [!NOTE]
> Kuruluş Yönetimi veya Alıcı Yönetimi rol grubunun üyesiyseniz, kullanıcı posta kutusunu şirket içi paylaşılan posta kutusuna değiştirmek için Exchange Yönetim Kabuğu'nı kullanabilirsiniz. Örneğin, `Set-Mailbox -Identity mailbox1@contoso.com -Type Shared`.

## <a name="related-content"></a>İlgili içerik

[Paylaşılan posta kutuları hakkında](about-shared-mailboxes.md) (makale)\
[Paylaşılan posta kutusu oluşturma](create-a-shared-mailbox.md) (makale)\
[Paylaşılan posta kutusunu yapılandırma](configure-a-shared-mailbox.md) (makale)\
[Paylaşılan posta kutusundan lisans kaldırma](remove-license-from-shared-mailbox.md) (makale)\
[Paylaşılan posta kutularıyla ilgili sorunları çözme](resolve-issues-with-shared-mailboxes.md) (makale)
