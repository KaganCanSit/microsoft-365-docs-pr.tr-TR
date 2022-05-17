---
title: Eski çalışanı kaldırma - Genel Bakış
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- SPO_Content
ms.custom:
- MSStore_Link
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- AdminTemplateSet
- m365solution-removeemployee
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
description: Eski bir çalışanın oturum açmaması, kuruluş verilerinin güvenliğini sağlamaması ve diğer çalışanların e-posta ve OneDrive verilerine erişmesine izin vermemesi için Microsoft 365 erişimini engelleyin.
ms.openlocfilehash: 3bff5812d1efd6b38f05303de7ec2c078b31cf01
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65436327"
---
# <a name="overview-remove-a-former-employee-and-secure-data"></a>Genel bakış: Eski bir çalışanı ve güvenli verileri kaldırma

Sık sık aldığımız bir soru şudur: "Bir çalışan kuruluşumdan ayrıldığında verilerin güvenliğini sağlamak ve erişimi korumak için ne yapmalıyım?" Bu makale serisinde, bu kullanıcıların Microsoft 365 oturum açamamaları için Microsoft 365 erişimi nasıl engelleyebileceğiniz, kuruluş verilerinin güvenliğini sağlamak için atılması gereken adımlar ve diğer çalışanların e-posta ve OneDrive verilerine erişmesine nasıl izin verebileceğiniz açıklanır.

> [!TIP]
> Bu konuda verilen adımlarla ilgili yardıma ihtiyacınız varsa[bir Microsoft küçük işletme uzmanıyla çalışmayı](https://go.microsoft.com/fwlink/?linkid=2186871) göz önünde bulundurun. İşletme Yardımı ile, işletmenizi büyütürken katılımdan gündelik kullanıma kadar her aşamada siz ve çalışanlarınız günün 24 saati küçük işletme uzmanlarına erişebilirsiniz.

## <a name="before-you-begin"></a>Başlamadan önce

Bu çözümdeki adımları tamamlamak için genel yönetici olmanız gerekir.

Bu serideki adımları tamamlamak için bu Microsoft 365 özelliklerini ve özelliklerini kullanırsınız.

|Ürün veya bileşen|Yetenek veya özellik|
|---|---|
|Microsoft 365 yönetici merkezi|Posta kutusunu dönüştürme, e-postayı iletme, erişimi iptal etme, kullanıcıyı kaldırma |
|Exchange yönetim merkezi|Kullanıcıyı engelle, e-posta erişimini engelle, cihazı temizle |
|OneDrive ve SharePoint |Diğer kullanıcılara erişim verme |
|Outlook|Pst dosyalarını içeri aktarma, posta kutusu ekleme |
|Active Directory|Karma ortamlarda kullanıcıları kaldırma |


## <a name="solution-remove-a-former-employee"></a>Çözüm: Eski çalışanı kaldırma

> [!IMPORTANT]
> Bu çözümdeki adımları numaralandırmış olsak da ve tam sırayı kullanarak çözümü tamamlamanıza gerek olmasa da, adımları bu şekilde gerçekleştirmenizi öneririz.

:::image type="content" source="../../media/delete-user-account.png" alt-text="Ekran görüntüsü: Kuruluşunuzdan eski bir çalışanı kaldırma adımları":::

<br>

****

|Adım|Neden yapılmalı|
|---|---|
|[1. Adım - Eski bir çalışanın oturum açmasını engelleme ve Microsoft 365 hizmetlerine erişimi engelleme](remove-former-employee-step-1.md)|Bu, eski çalışanınızın Microsoft 365 oturum açmasını engeller ve kişinin Microsoft 365 hizmetlerine erişmesini engeller.|
|[2. Adım - Eski çalışanın posta kutusunun içeriğini kaydetme](remove-former-employee-step-2.md)|Bu, çalışanın işini devralacak olan kişi veya dava varsa yararlıdır.|
|[3. Adım - Eski bir çalışanın mobil cihazını silme ve engelleme](remove-former-employee-step-3.md)|Telefondan veya tabletten iş verilerinizi kaldırır.|
|[4. Adım - Eski çalışanın e-postasını başka bir çalışana iletme veya paylaşılan posta kutusuna dönüştürme](remove-former-employee-step-4.md)|Bu işlem, eski çalışanınızın e-posta adresini etkin tutmanızı sağlar. Hala eski çalışanın adresine e-posta gönderen müşterileriniz veya iş ortaklarınız varsa, bu sayede işi devralan kişiye ulaşabilirler.|
|[5. Adım - Başka bir çalışana OneDrive ve Outlook verilerine erişim verme](remove-former-employee-step-5.md)|Kullanıcının yalnızca lisansını iptal eder ancak hesabını silmezseniz kullanıcının OneDrive'da bulunan içeriğine, 30 gün geçtikten sonra bile erişebilirsiniz. <p> Hesabı silmeden önce OneDrive ve Outlook başka bir kullanıcıya erişim vermeniz gerekir. Bir çalışanın hesabını sildikten sonra, OneDrive ve Outlook içeriği **30** gün boyunca saklanır. Ancak bu 30 gün boyunca kullanıcının hesabını geri yükleyebilir ve içeriğine erişebilirsiniz. Kullanıcının hesabını geri yüklerseniz, OneDrive ve Outlook içeriği 30 gün sonra bile sizin için erişilebilir kalır.| 
|[6. Adım - Eski bir çalışandan Microsoft 365 lisansını kaldırma ve silme](remove-former-employee-step-6.md)|Lisansı kaldırdığınızda, başka birine atayabilirsiniz. Öte yandan, lisansı silebilir ve bu şekilde başka birini işe alana kadar lisans için ödeme yapmazsınız.  <p> Lisansı kaldırdığınızda veya sildiğinizde, kullanıcının eski e-postası, kişileri ve takvimi **30 gün** boyunca korunur, sonrasında kalıcı olarak silinir. Lisansı kaldırır veya siler ancak hesabı silmezseniz, kullanıcının OneDrive'da bulunan içeriğine 30 gün geçtikten sonra bile erişebilirsiniz.  |
|[7. Adım - Eski çalışanın kullanıcı hesabını silme](remove-former-employee-step-7.md)|Bu işlem hesabı yönetim merkezinizden kaldırır. Ortamı temiz tutmanızı sağlar.|

 ## <a name="watch-delete-a-user"></a>İzleyin: Kullanıcıyı silme

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfR?autoplay=false]

Bir çalışan şirketten ayrıldığında, bu çalışanı iş için Microsoft 365 kaldırmanız gerekir. Bunu yapmadan önce, şirket dosyalarına erişmelerini engellemeniz, oluşturdukları belgeleri korumanız ve bir kullanıcıyı kaldırmayla ilişkili diğer birkaç yönetici görevini gerçekleştirmeniz gerekir.

1. Yönetim merkezinde **Kullanıcılar'ı ve** **ardından Etkin kullanıcılar'ı** seçin.
1. Kaldırmak istediğiniz kullanıcıyı seçin ve ardından **Kullanıcıyı sil'i** seçin.
1. Lisansını kaldırmak için kutuyu işaretleyin ve e-posta diğer adlarını kaldırmak için kutuyu işaretleyin.
1. Başka bir kullanıcıya eski çalışanın e-postasına erişim vermek için kutuyu işaretleyin ve **Kullanıcı seç'i seçip e-posta seçeneklerini ayarlayın**.
1. İlişkili e-posta diğer adlarını kaldırmak için diğer adlarının yanındaki **X'i** seçin.
1. Paylaşılan posta kutusu bilgilerini gözden geçirin ve **Son'u** seçin.
1. Seçeneklerinizin doğru ayarlandığını onaylayın ve **Ata ve dönüştür'ü** seçin.
1. Sonuçlarınızı gözden geçirin ve **Kapat'ı** seçin.

Bir kullanıcıyı kaldırdıktan sonra hesabını geri yüklemek için en fazla 30 gününüz olur.
## <a name="related-content"></a>İlgili içerik

[Kullanıcıyı geri yükleme](restore-user.md) (makale)\
[Microsoft 365 yeni çalışan ekleme](add-new-employee.md) (makale)\
[Kullanıcılara lisans atama](../manage/assign-licenses-to-users.md) (makale)\
[Kullanıcılardan lisans atamalarını kaldırma](../manage/remove-licenses-from-users.md) (makale)
