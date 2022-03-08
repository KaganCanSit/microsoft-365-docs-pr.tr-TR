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
description: Eski bir çalışanı iş yerlerinden kaldırmak ve kuruluş verilerini Microsoft 365 için bu çözümde yer alan adımları izleyin.
ms.openlocfilehash: 799a946c85da94fcc3d9e53a4015697d124192ce
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63315183"
---
# <a name="overview-remove-a-former-employee-and-secure-data"></a>Genel bakış: Eski çalışanı kaldırma ve verilerin güvenliğini sağlama

Şu soruyla sık sık karşılarız: "Bir çalışan kuruluşumdan ayrıldığında verilerin güvenliğini sağlamak ve erişimi korumak için ne yapabilirim?" Bu makale serisinde, bu kullanıcıların Microsoft 365'te oturum a açmasını engellemek için Microsoft 365 erişiminin nasıl engellenmiş olduğu, kuruluş verilerini güvenlik altına almak için atılması gereken adımlar ve diğer çalışanların e-posta ve OneDrive izin vermeleri açıklanmıştır.

> [!TIP]
> Bu konudaki adımlarda yardıma ihtiyacınız varsa, [Microsoft küçük işletme uzmanıyla çalışmayı göz önünde bulundurabilirsiniz](https://go.microsoft.com/fwlink/?linkid=2186871). İş Yardımı ile, işe alımtan günlük kullanıma kadar işlerinizi büyüttükçe siz ve çalışanlarınız küçük işletme uzmanlarına 24 saat erişim elde ediyor.

## <a name="before-you-begin"></a>Başlamadan önce

Bu çözümde adımları tamamlamak için genel yönetici olmak gerekir.

Bu serinin adımlarını tamamlamak için, bu özellikleri Microsoft 365 kullanabilirsiniz.

|Ürün veya bileşen|Özellik veya özellik|
|---|---|
|Microsoft 365 yönetici merkezi|Posta kutusunu dönüştürme, e-posta iletme, erişimi iptal etme, kullanıcı kaldırma |
|Exchange merkezi|Kullanıcı engelleme, e-posta erişimini engelleme, cihazı temizleme |
|OneDrive ve SharePoint |Diğer kullanıcılara erişim verme |
|Outlook|Pst dosyalarını içeri aktarma, posta kutusu ekleme |
|Active Directory|Karma ortamlarda kullanıcıları kaldırma |


## <a name="solution-remove-a-former-employee"></a>Çözüm: Eski bir çalışanı kaldırma

> [!IMPORTANT]
> Bu çözümde adımları numaralandık ve tam sırayı kullanarak çözümü tamamlamanız gerekse de, adımları bu şekilde yapmanizi öneririz.

:::image type="content" source="../../media/delete-user-account.png" alt-text="Ekran görüntüsü: Eski bir çalışanı kuruluştan kaldırma adımları":::

<br>

****

|Adım|Neden yapılmalı|
|---|---|
|[1. Adım - Eski bir çalışanın oturum açmasını ve bu hizmetlere erişimi Microsoft 365 engelleme](remove-former-employee-step-1.md)|Bu, eski çalışanın e-posta Microsoft 365 açmasını engeller ve bu kişinin Microsoft 365 engeller.|
|[2. Adım - Eski çalışanın posta kutusunun içeriğini kaydetme](remove-former-employee-step-2.md)|Bu, çalışanın çalışmalarını alacak kişi için veya bir dava varsa yararlı olur.|
|[3. Adım - Eski çalışanın mobil cihazı temizleme ve engelleme](remove-former-employee-step-3.md)|Telefondan veya tabletten iş verilerinizi kaldırır.|
|[4. Adım - Eski bir çalışanın e-posta adresini başka bir çalışana iletme veya paylaşılan posta kutusuna dönüştürme](remove-former-employee-step-4.md)|Bu işlem, eski çalışanınızın e-posta adresini etkin tutmanızı sağlar. Hala eski çalışanın adresine e-posta gönderen müşterileriniz veya iş ortaklarınız varsa, bu sayede işi devralan kişiye ulaşabilirler.|
|[5. Adım - Başka bir çalışana kişisel veriler OneDrive verileri Outlook verme](remove-former-employee-step-5.md)|Kullanıcının yalnızca lisansını iptal eder ancak hesabını silmezseniz kullanıcının OneDrive'da bulunan içeriğine, 30 gün geçtikten sonra bile erişebilirsiniz. <p> Hesabı smeden önce bu kullanıcının e-posta hesabına erişim OneDrive Outlook kullanıcıya erişim izni verebilirsiniz. Bir çalışanın hesabını sildikten sonra, çalışma sayfalarındaki OneDrive Outlook **30 gün boyunca korunur**. Bu 30 gün boyunca kullanıcının hesabını geri yükleyebilir ve içeriğine erişebilirsiniz. Kullanıcının hesabını geri yükledikten sonra, OneDrive Outlook içeriği 30 gün sonra bile erişilebilir durumda kalır.| 
|[6. Adım - Eski bir Microsoft 365 lisansını kaldırma ve silme](remove-former-employee-step-6.md)|Lisansı kaldırdığınızda, başka birine atayabilirsiniz. Öte yandan, lisansı silebilir ve bu şekilde başka birini işe alana kadar lisans için ödeme yapmazsınız.  <p> Lisansı kaldırdığınızda veya sildiğinizde, kullanıcının eski e-postası, kişileri ve takvimi **30 gün** boyunca korunur, sonrasında kalıcı olarak silinir. Lisansı kaldırır veya siler ancak hesabı silmezseniz, kullanıcının OneDrive'da bulunan içeriğine 30 gün geçtikten sonra bile erişebilirsiniz.  |
|[7. Adım - Eski çalışanın kullanıcı hesabını silme](remove-former-employee-step-7.md)|Bu işlem, hesabı yönetim merkezinden kaldırır. Ortamı temiz tutmanızı sağlar.|

 ## <a name="watch-delete-a-user"></a>İzle: Kullanıcı silme

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfR?autoplay=false]

Bir çalışan şirketten ayrıldığında bu çalışanı iş için Microsoft 365 kaldırmanız gerekir. Bunu öncesinde, bu kullanıcının şirket dosyalarına erişimini engellemeniz, oluşturduğu belgeleri korumalı ve kullanıcı kaldırmayla ilişkilendirilmiş diğer birkaç yönetici görevlerini gerçekleştirebilirsiniz.

1. Yönetim merkezinde Kullanıcılar'ı **ve ardından** Etkin **kullanıcılar'ı seçin**.
1. Kaldırmak istediğiniz kullanıcı seçin ve sonra da Kullanıcı **sil'i seçin**.
1. Lisanslarını kaldırmak için ve e-posta diğer adlarını kaldırmak için onay kutusunu işaretleyin.
1. Başka bir kullanıcıya eski çalışanın e-postası için erişim vermek için kutuyu işaretleyin ve Bir kullanıcı seçin **ve e-posta seçeneklerini ayarlayın**.
1. İlişkili e-posta diğer adlarını kaldırmak için, diğer **adların yanındaki X'i** seçin.
1. Paylaşılan posta kutusu bilgilerini gözden geçirip Son'a **seçin**.
1. Seçeneklerinizin doğru ayar olduğunu onaylayın ve Ata ve **dönüştür'e tıklayın**.
1. Sonuçlarınızı gözden geçirerek Kapat'ı **seçin**.

Bir kullanıcıyı kaldırdikten sonra, hesabını geri yüklemek için 30 gün kadar süre vardır.
## <a name="related-content"></a>İlgili içerik

[Bir kullanıcı geri yükleme](restore-user.md) (makale)\
[yeni çalışan ekleme (Microsoft 365](add-new-employee.md))\
[Kullanıcılara lisans atama](../manage/assign-licenses-to-users.md) (makale)\
[Kullanıcılardan lisans atamalarını iptal et](../manage/remove-licenses-from-users.md) (makale)
