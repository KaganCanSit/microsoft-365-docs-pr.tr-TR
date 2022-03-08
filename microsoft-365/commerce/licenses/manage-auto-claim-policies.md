---
title: Otomatik talep ilkelerini yönetme
f1.keywords:
- CSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: yinggiy, pablom
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_licensing
- AdminSurgePortfolio
description: Belirli uygulamalar için otomatik olarak lisans atayanın otomatik talep ilkelerinin nasıl oluşturul ve yönetilir öğrenin.
search.appverid: MET150
ms.date: 04/06/2021
ms.openlocfilehash: d6cb3d78de914e84e831947089aeadf277e72ddf
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63321103"
---
# <a name="manage-auto-claim-policies"></a>Otomatik talep ilkelerini yönetme

Otomatik talep ilkesi, kullanıcıların bir uygulamada ilk kez oturum alıkan bir ürün için otomatik olarak lisans talep  ettiğine olanak sağlar. Yönetici olarak, kullanıcılara genellikle el ile veya grup tabanlı lisanslama kullanarak lisans atarsınız. Otomatik talep ilkelerini kullanarak, kullanıcıların otomatik olarak lisans talep  ettiği ürünleri yönetirsiniz. Ayrıca, bu lisansların hangi ürünlerden gelip gelmelerini de kontrolabilirsiniz.

> [!IMPORTANT]
> Otomatik talep e-posta ilkeleri şu anda yalnızca Microsoft Teams. Gelecekte daha fazla ürün kullanılabilir olacaktır.

## <a name="before-you-begin"></a>Başlamadan önce

Otomatik talep ilkelerini oluşturmak ve yönetmek için Genel, Kullanıcı veya Lisans yöneticisi olun. Daha fazla bilgi için bkz[. Microsoft 365 rolleri hakkında](../../admin/add-users/about-admin-roles.md).

## <a name="turn-the-auto-claim-policy-feature-on-or-off"></a>Otomatik talep ilkesi özelliğini açma veya kapatma

Varsayılan olarak, otomatik talep politikası özelliği kapalıdır. Özelliği kullanamadan önce bu özelliği açabilirsiniz. Özelliği açtırdikten sonra bir otomatik talep politikası oluşturabilirsiniz.

### <a name="turn-on-auto-claim-policies"></a>Otomatik talep ilkelerini açma

1. Yönetim merkezinde Fatura Lisansları sayfasına **gidin** \> ve ardından Otomatik talep edin <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">ilkesi sekmesini</a> seçin.
2. Sayfanın orta tarafından Ayarı aç **düğmesini** seçin.

### <a name="turn-off-auto-claim-policies"></a>Otomatik talep ilkelerini kapatma

Otomatik talep ilkesi ayarını yalnızca Genel yönetici kapatabilirsiniz.

1. Yönetim merkezinde Kuruluş **ayarları Ayarlar** \> gidin.<a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank"></a>
2. Tablonun alt kısmında, Kullanıcıya ait uygulamalar **ve hizmetler'i seçin**.
3. Sağ bölmede, İlk kez oturum alıkan kullanıcıların otomatik olarak lisans talep **sinesine izin ver kutusunu temizleyin**.

Zaten etkin bir ilkeniz varsa ancak başka kullanıcıların lisans talep etmelerini istemiyorsanız, [ilkeyi kapatın](#turn-a-policy-on-or-off). Otomatik talep politikasını kapatarak, bu noktadan sonra artık hiçbir kullanıcı lisans talep ede çevirmez. Zaten lisans talep eden kullanıcılar lisanslarını kaybetmez.

## <a name="create-an-auto-claim-policy"></a>Otomatik talep ilkesi oluşturma

Otomatik <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">talep e-posta ilkesi</a> sekmesi, sizin oluştur ilkeleri listeler. Bu sekmede şunları görebilirsiniz: ilkenin adı, ilkeyle ilişkilendirilmiş uygulama, ilkeye atanan ürün, kullanılabilir lisansların sayısı ve ilkenin durumu.

Bir otomatik talep ilkesi 2013'e yedek ürün  eklersiniz. Birincil ürün lisans dışında olursa, yedek ürün kullanıcılara lisans atamak için kullanılır. En çok dört yedek ürün [ekleyebilir ve bunların kullanılma sıralarını değiştirebilirsiniz](#change-the-assigning-order-for-backup-products). Daha fazla bilgi edinmek için bkz [. Yedek ürünleri ekleme veya kaldırma](#add-or-remove-backup-products).

> [!NOTE]
> Şu anda, tek bir otomatik talep politikası oluşturabilirsiniz. Bu özelliği daha fazla ürün kullananın, oluşturabilecek ilke sayısı artacaktır.

1. Yönetim merkezinde Fatura Lisansları sayfasına **gidin** \> ve ardından Otomatik talep edin <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">ilkesi sekmesini</a> seçin.
2. İlke **ekle'yi seçin**.
3. Bu otomatik **talep politikasının adını yazın** sayfasında, ilke için bir ad girin ve Ardından Sonraki'yi **seçin**.
4. Otomatik **talep etme uygulaması ve ürün ayarlama sayfasında** , lisans ataması için bir uygulama ve abonelik seçin.
5. Yedek ürün eklemek için, Bu ilkeye yedek ürün ekle'yi **seçin** ve ardından listeden ürünü seçin.
6. **İleri**'yi seçin.
7. Uygulamaları **seçin sayfasında** , hariç tutulacak veya lisansa dahil olacak uygulamaların kutularını temizleyin veya seçin, sonra da Sonraki'yi **seçin**.
8. Bir veya daha fazla yedek ürün eklediysanız, her ürün için 7. adımı yinelayın. Aksi takdirde, 9. adıma gidin.
9. Gözden Geçir **ve bitir sayfasında** , yeni ilke bilgilerini doğrulayın, gerekli değişiklikleri yapın ve ardından İlke **oluştur'a tıklayın**.
10. **Kapat**'ı seçin.

## <a name="turn-a-policy-on-or-off"></a>İlkeyi açma veya kapatma

Bir ilkeyi devre dışı seniz, artık kullanıcılar o ilke kapsamında lisans talep edeleye sahip olmaz. Bu değişiklik, o ilke kapsamında zaten lisans talep eden kullanıcıları etkilemez.

1. Yönetim merkezinde Fatura Lisansları sayfasına **gidin** \> ve ardından Otomatik talep edin <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">ilkesi sekmesini</a> seçin.
2. Düzenlemek istediğiniz ilkeyi seçin.
3. Ayrıntılar bölmesinde, Bu **ilkeyi aç veya kapat'ın** altında onay kutusunu seçin veya temizleyin.
4. Ayrıntılar **bölmesini** kapatmak için Kaydet'i seçin.

## <a name="edit-the-policy-friendly-name"></a>İlke kolay adını düzenleme

1. Yönetim merkezinde Fatura Lisansları sayfasına **gidin** \> ve ardından Otomatik talep edin <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">ilkesi sekmesini</a> seçin.
2. Düzenlemek istediğiniz ilkeyi seçin.
3. Ayrıntılar bölmesinde, İlke adı **bölümünde Düzenle'yi** **seçin**.
4. Yeni bir ilke adı girin ve ardından Kaydet'i **seçin**.
5. Ayrıntılar **bölmesini** kapatmak için Kaydet'i seçin.

## <a name="add-or-remove-backup-products"></a>Yedek ürünler ekleme veya kaldırma

bir ilke seniz, ilkeye ürün eklersiniz. Bundan sonra, lisanslar o lisans havuzundan kullanıcılara otomatik olarak atanır. Otomatik talep politikası için istediğiniz zaman ürün ekleyebilir veya kaldırabilirsiniz. İlkeyle ilişkilendirilmiş tek bir ürününüz varsa, eklemeniz gereken tüm ürünler yedek ürün olarak kabul edilir. İlk üründen kullanılabilir lisans sayısı kullanılırken, ilke, lisansları atamak için listede bir sonraki yedek ürünü kullanır. Ürünlerin [listesini olduğu gibi yeniden](#change-the-assigning-apps-and-services) sıraabilirsiniz.

Yedek ürünü kaldırdığınız zaman, bu ürün artık lisansları atamak için kullanılmaz. Var olan lisansa sahip olan kullanıcılar bu lisansa sahip ancak bu ürün için hiçbir yeni kullanıcı lisans alamz.

> [!NOTE]
> Otomatik talep politikası en az bir ürün içerebilir. bir ilkeden tüm ürünleri kaldırabilirsiniz. Artık belirli bir otomatik talep ilkesinden lisans atamak istemiyorsanız, [ilkeyi kapatın](#view-an-auto-claim-policy-report).

### <a name="add-a-backup-product"></a>Yedek ürün ekleme

1. Yönetim merkezinde Fatura Lisansları sayfasına **gidin** \> ve ardından Otomatik talep edin <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">ilkesi sekmesini</a> seçin.
2. Düzenlemek istediğiniz ilkeyi seçin.
3. Ayrıntılar bölmesinde, en altta Bu ilkeye **yedek ürün ekle'yi seçin**.
    > [!NOTE]
    > Bu bağlantıyı görmüyorsanız, hesabınızla ilişkilendirilmiş yalnızca bir ürün vardır.
4. Ürün **ekle bölmesinde,** ilkeye eklemek üzere bir ürün seçmek için açılır pencereyi kullanın ve ardından Ekle'yi **seçin**.
5. Ayrıntılar **bölmesini** kapatmak için Kaydet'i seçin.

### <a name="remove-a-backup-product"></a>Yedek ürünü kaldırma

1. Yönetim merkezinde Fatura Lisansları sayfasına **gidin** \> ve ardından Otomatik talep edin <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">ilkesi sekmesini</a> seçin.
2. Düzenlemek istediğiniz ilkeyi seçin.
3. Ayrıntılar bölmesinde, en altta Ürünü **kaldır'ı seçin**.
4. **İlkeden ürün kaldır bölmesinde**, kaldırmak istediğiniz ilkenin kutusunu seçin ve sonra da Kaydet'i **seçin**.
5. Ayrıntılar bölmesini kapatın.

## <a name="change-the-assigning-apps-and-services"></a>Uygulama ve hizmet atamayı değiştirme

Her ürünle ilişkilendirilmiş bir uygulama ve hizmet koleksiyonu vardır. Otomatik talep talebi ilkenize dahil olan her ürün için, bir kullanıcıya otomatik olarak lisans atandığı zaman hangi uygulama ve hizmetlerin dahil edilir olduğunu belirtebilirsiniz.

1. Yönetim merkezinde Fatura Lisansları sayfasına **gidin** \> ve ardından Otomatik talep edin <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">ilkesi sekmesini</a> seçin.
2. Düzenlemek istediğiniz ilkeyi seçin.
3. Ayrıntılar bölmesinde, Uygulamalar ve **hizmetler'in altında Düzenle'yi** **seçin**.
4. Uygulamalar **ve hizmetler bölmesindeki** Ürün açılan **listesinden** tek bir ürün seçin veya Tüm ürünler'i **seçin**.
5. Kullanıcıların erişmesi veya erişimi olmadığını görmek istediğiniz uygulama ve hizmetlerin kutularını işaretleyin veya temizleyin.
6. Bitirdikten sonra **Kaydet'i seçin** ve sonra ayrıntılar bölmesini kapatın.

## <a name="change-the-assigning-order-for-backup-products"></a>Yedek ürünler için atama siparişlerini değiştirme

İlkeye atanmış yedek ürünleriniz varsa, kullanıcıların uygulamada oturum atayarak lisansları atamak için kullanılma sıralarını değiştirebilirsiniz.

1. Yönetim merkezinde Fatura Lisansları sayfasına **gidin** \> ve ardından Otomatik talep edin <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">ilkesi sekmesini</a> seçin.
2. Düzenlemek istediğiniz ilkeyi seçin.
3. Ayrıntılar bölmesindeki Ürün lisansları bölümünde, taşımak istediğiniz ürünün yanındaki kutuyu seçin ve sonra da Yukarı taşı veya Aşağı  **taşı'ya tıklayın**.
4. Yeniden sıralamak istediğiniz her ürün için 3. adımı yinelayın.
5. Ürünleri yeniden sıralamayı bitirdikten sonra ayrıntılar bölmesini kapatmak **için Kaydet'i** seçin.

## <a name="view-an-auto-claim-policy-report"></a>Otomatik talep ilke raporunu görüntüleme

1. Yönetim merkezinde Fatura Lisansları sayfasına **gidin** \> ve ardından Otomatik talep edin <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">ilkesi sekmesini</a> seçin.
2. Raporu **görüntüle'yi seçin**. Otomatik **talep edin ilke raporu sayfasında** , son 90 gün içinde her ilkeden atanmış tüm lisanslar görüntülenir. Varsayılan olarak, sayfada son 90 gün görüntülenir.
3. Gösterilen zaman dönemini değiştirmek için Son **30 gün** açılan listesini seçin. Son 1, 7, 30 ve 90 günlük raporları görüntüabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Oluşturduğunuz ilkeler altında lisans **talep** eden kullanıcıların listesini görmek için, düzenli aralıklarla Otomatik talep politikası sekmesine dönebilirsiniz.

## <a name="related-content"></a>İlgili içerik

[Kullanıcılara lisans atama](../../admin/manage/assign-licenses-to-users.md) (makale)\
[Abonelik lisansları satın alma veya kaldırma](buy-licenses.md) (makale)\
[Abonelikleri ve lisansları anlama](subscriptions-and-licenses.md) (makale)
