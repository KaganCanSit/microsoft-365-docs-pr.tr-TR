---
title: Fatura bildirimlerini ve fatura eklerini yönetme
f1.keywords:
- CSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
ms.reviewer: prkalid, guyb
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- okr_SMB
- AdminSurgePortfolio
- commerce_billing
search.appverid:
- MET150
description: Fatura bildirimi e-postalarını ve fatura eklerini kimlerin aldığını yönetmeyi öğrenin.
ms.date: 03/17/2021
ms.openlocfilehash: 0f33029d874ee3564eed272cbc670aacaf10b283
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985174"
---
# <a name="manage-billing-notifications-and-invoice-attachments"></a>Fatura bildirimlerini ve fatura eklerini yönetme

Fatura **bildirimleri sayfası,** organizasyonunız için faturalandırma bildirimi e-postalarını kimlerin aldığını yönetmenize olanak sağlar. Bu sayfada ayrıca, kuruluş [faturalarını e-posta eki olarak alma seçeneği de vardır](#receive-your-organizations-invoices-as-email-attachments).

## <a name="before-you-begin"></a>Başlamadan önce

Bu makalede açıklanan adımları yapmak için Genel yönetici olmalı. Faturalama yöneticileri, aşağıdaki bölümlerde da ifade edildiyseniz bu değişikliklerden bazıları yapabilirsiniz. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).

## <a name="change-the-language-you-receive-email-in"></a>E-postayı almak için dili değiştirme

Fatura bildirimi e-postaları, kurumuz tarafından tercih edilen dilde gönderilir. Tercih edilen dili değiştirmek için aşağıdaki adımları kullanın.

1. Fatura Microsoft 365 yönetim merkezi, **FaturaBilling** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=853212" target="_blank">bildirimleri sayfasına</a> gidin.
2. Fatura bildirimi **ayarları bölümünde Bildirim** ayarlarını **düzenle'yi seçin**.
3. Fatura bildirim **ayarları bölmesinde,** Tercih edilen **dil'in** altında kullanmak istediğiniz dili seçin ve ardından Kaydet'i **seçin**.

## <a name="change-who-receives-billing-notifications"></a>Fatura bildirimlerini kimin aldığını değiştirme

Tüm Genel ve Faturalama yöneticilerinin birincil ve alternatif e-posta adreslerine, kurum ödeme bildirimleri gönderilir. Hangi kullanıcıların Genel veya Faturalama yöneticisi rolüne sahip olduğunu değiştirmek için aşağıdaki adımları kullanın.

### <a name="assign-admin-roles-by-using-the-billing-notifications-page"></a>Fatura bildirimleri sayfasını kullanarak yönetici rolleri atama

1. Yönetim merkezinde **FaturaBilling bildirimleri** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=853212" target="_blank">sayfasına</a> gidin.
2. Fatura **bildirimlerini alan yöneticiler bölümünde** , açıklama metninde **Faturalama yöneticisi** veya **Genel yönetici** bağlantısını seçin.
3. Sağ bölmede, Atanan yöneticiler **sekmesinde Ekle'yi** **seçin**.
4. Yönetici **ekle bölmesinde** , kullanıcının görünen adını veya kullanıcı adını yazın ve ardından öneri listesinden bir kullanıcı seçin.
5. Bitirene kadar birden çok kullanıcı ekleyin.
6. **Kaydet**'i seçin. Kullanıcı atanan yöneticiler listesine eklenir.

### <a name="remove-admin-roles-by-using-the-billing-notifications-page"></a>Fatura bildirimleri sayfasını kullanarak yönetici rollerini kaldırma

1. Yönetim merkezinde **FaturaBilling bildirimleri** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=853212" target="_blank">sayfasına</a> gidin.
2. Fatura **bildirimlerini alan yöneticiler bölümünde** , açıklama metninde **Faturalama yöneticisi** veya **Genel yönetici** bağlantısını seçin.
3. Sağ bölmede, Atanan yöneticiler **sekmesinde** rolden kaldıracak kullanıcıları seçin ve sonra da Kaldır'ı **seçin**.
4. Onay kutusunda Kaldır'ı **seçin**. Kullanıcı atanan yöneticiler listesinden kaldırılır.

## <a name="change-the-email-addresses-for-admins"></a>Yöneticilerin e-posta adreslerini değiştirme

Kuruluşta diğer yöneticilerin birincil ve alternatif e-posta adreslerini değiştirmek için aşağıdaki adımları kullanın.

> [!NOTE]
> Faturalama yöneticileri kendi birincil ve alternatif e-posta adreslerini değiştirebilir, ancak diğer yöneticiler için değiştiremezler.

1. Yönetim merkezinde **FaturaBilling bildirimleri** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=853212" target="_blank">sayfasına</a> gidin.
2. Fatura **bildirimleri alan yöneticiler bölümünde** bir ad seçin.
3. Sağ bölmede, gerekirse birincil ve alternatif e-posta adresini ekleyin veya güncelleştirin, sonra da Kaydet'i **seçin**.

## <a name="change-your-organizations-contact-email"></a>Kuruluşun kişi e-posta adresini değiştirme

Genel yöneticilerinize ve Faturalama yöneticilerinize ek olarak, fatura bildirimlerini de kurumnizin iletişim e-posta adresine göndeririz. E-posta adresini değiştirmek için aşağıdaki adımları kullanın.

1. Yönetim merkezinde **FaturaBilling bildirimleri** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=853212" target="_blank">sayfasına</a> gidin.
2. Fatura **bildirimlerini alan kuruluş ilgili kişisi'nin** altında kuruluş ilgili kişisi seçin.
3. Sağ bölmede, kullanmak istediğiniz e-posta adresini yazın ve ardından Kaydet'i **seçin**.

## <a name="receive-your-organizations-invoices-as-email-attachments"></a>Kuruluş faturalarını e-posta eki olarak alma

> [!NOTE]
> Faturalama yöneticileri de bu bölümdeki adımları uygulayın.

Yeni bir fatura hazır olduğunda, fatura bildirimi e-postanıza, kuruluş faturalarının bir kopyasını PDF dosyası olarak iliştirebilirsiniz. Faturaları ek olarak almak için aşağıdaki adımları kullanın.

1. Yönetim merkezinde **FaturaBilling bildirimleri** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=853212" target="_blank">sayfasına</a> gidin.
2. Fatura **bildirim ayarları'nın altında** Bildirim ayarlarını **düzenle'yi seçin**.
3. Fatura bildirim **ayarları bölmesindeki** Fatura e-postanıza **PDF ekleyin'in** altında onay kutusunu işaretleyin ve ardından Kaydet'i **seçin**.

Fatura ekini istediğiniz zaman almayı durdurmak için, yukarıdaki adımları izleyin ve 3. adımda Fatura e-postanıza **PDF** ekle onay kutusunu temizleyin.

## <a name="what-if-i-have-a-billing-profile"></a>Fatura profilim varsa ne olacak?

Fatura profiliniz varsa, bu makalede açıklanan adımlardan bazıları aboneliklerin bazıları için biraz farklı olabilir. Bu bölümde bu farklar açık almaktadır. [Fatura profilim olup olduğunu nasıl bilebilirsiniz?](manage-billing-profiles.md)

### <a name="who-receives-billing-notifications"></a>Who bildirimleri alır mısınız?

Ödeme bildirimi e-postaları, aşağıdaki rollerden biri atanan kullanıcılar için birincil ve alternatif e-posta adreslerine gönderilir:

- Ödeme profili sahibi
- Ödeme profili katılımcısı
- Fatura yöneticisi

Fatura profili rolleri ve bu rolleri yönetme hakkında daha fazla bilgi edinmek için bkz. [Azure'daki Microsoft Müşteri Sözleşmesi yönetim rollerini anlama](/azure/cost-management-billing/manage/understand-mca-roles).

Kuruluşun fatura bildirimlerini kimlerin aldığını değiştirmek için aşağıdaki adımları kullanarak kullanıcılara atanan rolleri değiştirebilirsiniz.

1. Yönetim merkezinde <a href="https://go.microsoft.com/fwlink/p/?linkid=2102895" target="_blank">BillingBills</a> **ve** >  payments & gidin.
2. Fatura **profili sekmesinde** bir fatura profili seçin.
3. Fatura profili **rolleri bölümünde**, Fatura profili sahibi, Fatura **profili katılımcısı** veya **Fatura yöneticisi için rol attay veya** **kaldır.**

### <a name="receive-invoices-as-email-attachments"></a>Faturaları e-posta eki olarak alma

Faturalarınızı fatura bildirimlerinize ek olarak almak için aşağıdaki adımları kullanarak belirli bir fatura profili için bu ayarı açın.

1. Yönetim merkezinde <a href="https://go.microsoft.com/fwlink/p/?linkid=2102895" target="_blank">BillingBills</a> **ve** >  payments & gidin.
2. Ödeme **profilleri sekmesini seçin** ve sonra da listeden bir fatura profili seçin.
3. Fatura profili ayrıntıları sayfasındaki E-posta **ekleri için faturaları al altından** iki durumlu düğmeyi Açık olarak **seçin**.

## <a name="related-content"></a>İlgili içerik

[Faturanızı veya faturanızı görüntüleme](view-your-bill-or-invoice.md) (makale)\
[Meksika'daki Microsoft 365 için fatura bilgileri](mexico-billing-info.md) (makale) \
[İş için faturanızı veya faturanızı Microsoft 365 (](understand-your-invoice2.md)makale)\
[Aynı anda kullanıcı ekleme ve lisans atama](../../admin/add-users/add-users.md) (makale)
