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
description: Belirli uygulamalar için kullanıcılara otomatik olarak lisans atayan otomatik talep ilkeleri oluşturmayı ve yönetmeyi öğrenin.
search.appverid: MET150
ms.date: 04/06/2021
ms.openlocfilehash: 76f2742dc97f880c8044def269e3e9517ea4605c
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66493796"
---
# <a name="manage-microsoft-teams-auto-claim-policies"></a>Microsoft Teams otomatik talep ilkelerini yönetme

Otomatik talep ilkesi, kullanıcıların bir uygulamada ilk kez oturum açtıklarında bir ürün için otomatik olarak lisans talep etmelerini sağlar. Yönetici olarak genellikle kullanıcılara el ile veya grup tabanlı lisanslama kullanarak lisans atarsınız. Otomatik talep ilkelerini kullanarak, kullanıcıların otomatik olarak lisans talep ettiği ürünleri yönetirsiniz. Ayrıca bu lisansların hangi ürünlerden geldiğini de denetleyebilirsiniz.

> [!IMPORTANT]
> Otomatik talep ilkeleri şu anda yalnızca Microsoft Teams için kullanılabilir. Gelecekte daha fazla ürün kullanıma sunulacaktır.

## <a name="before-you-begin"></a>Başlamadan önce

Otomatik talep ilkeleri oluşturmak ve yönetmek için Genel, Kullanıcı veya Lisans yöneticisi olmanız gerekir. Daha fazla bilgi için bkz. [Microsoft 365 yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).

## <a name="turn-the-auto-claim-policy-feature-on-or-off"></a>Otomatik talep ilkesi özelliğini açma veya kapatma

Varsayılan olarak, otomatik talep ilkesi özelliği kapalıdır. Özelliği kullanabilmeniz için önce açmanız gerekir. Özelliği açtıktan sonra otomatik talep ilkesi oluşturabilirsiniz.

### <a name="turn-on-auto-claim-policies"></a>Otomatik talep ilkelerini açma

1. Yönetim merkezinde **Faturalama** \> **Lisansları** sayfasına gidin ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">otomatik talep ilkesi</a> sekmesini seçin.
2. Sayfanın ortasında **Ayarı aç** düğmesini seçin.

### <a name="turn-off-auto-claim-policies"></a>Otomatik talep ilkelerini kapatma

Otomatik talep ilkesi ayarını yalnızca Genel yönetici kapatabilir.

1. Yönetim merkezinde **Ayarlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">Kuruluş ayarları</a> sayfasına gidin.
2. Tablonun alt kısmında **Kullanıcıya ait uygulamalar ve hizmetler'i** seçin.
3. Sağ bölmede **Kullanıcıların ilk kez oturum açtıklarında lisansları otomatik olarak talep etmesine izin ver** kutusunu temizleyin.

Zaten etkin bir ilkeniz varsa ancak daha fazla kullanıcının lisans talep etmesini istemiyorsanız, [ilkeyi kapatın](#turn-a-policy-on-or-off). Otomatik talep ilkesini kapattığınızda, artık hiçbir kullanıcı bu noktadan lisans talep etme iznine sahip olamaz. Zaten lisans talep eden kullanıcılar lisanslarını kaybetmez.

## <a name="create-an-auto-claim-policy"></a>Otomatik talep ilkesi oluşturma

<a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">Otomatik talep ilkesi</a> sekmesinde oluşturduğunuz ilkeler listelenir. Bu sekmede şunları görebilirsiniz: ilkenin adı, ilkeyle ilişkilendirilmiş uygulama, ilkeye atanan ürün, kullanılabilir lisans sayısı ve ilkenin durumu.

Otomatik talep ilkesi oluşturduğunuzda, buna bir yedek ürün ekleyebilirsiniz. Birincil ürünün lisansları bittiyse, kullanıcılara lisans atamak için yedekleme ürünü kullanılır. En fazla dört yedekleme ürünü ekleyebilir ve [bunların kullanılma sırasını değiştirebilirsiniz](#change-the-assigning-order-for-backup-products). Daha fazla bilgi için bkz [. Yedekleme ürünleri ekleme veya kaldırma](#add-or-remove-backup-products).

> [!NOTE]
> Şu anda yalnızca bir otomatik talep ilkesi oluşturabilirsiniz. Bu özelliği daha fazla ürün kullanabildiği sürece oluşturabileceğiniz ilke sayısı artar.

1. Yönetim merkezinde **Faturalama** \> **Lisansları** sayfasına gidin ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">otomatik talep ilkesi</a> sekmesini seçin.
2. **İlke ekle'yi** seçin.
3. **Bu otomatik talep ilkesini adlandır** sayfasında, ilke için bir ad girin ve **İleri'yi** seçin.
4. **Otomatik talep uygulaması ve ürün ayarla** sayfasında, lisans atamak için bir uygulama ve abonelik seçin.
5. Yedek ürün eklemek istiyorsanız **, Bu ilkeye yedek ürün ekle'yi** seçin ve ardından listeden ürünü seçin.
6. **İleri**'yi seçin.
7. **Uygulamaları seçin** sayfasında, uygulamaların lisansa dahil veya hariç tutulacak kutularını temizleyin veya seçin, ardından **İleri'yi** seçin.
8. Bir veya daha fazla yedekleme ürünü eklediyseniz, her ürün için 7. adımı yineleyin. Aksi takdirde 9. adıma gidin.
9. **Gözden geçir ve bitir** sayfasında yeni ilke bilgilerini doğrulayın, gerekli değişiklikleri yapın ve **İlke oluştur'u** seçin.
10. **Kapat**'ı seçin.

## <a name="turn-a-policy-on-or-off"></a>İlkeyi açma veya kapatma

Bir ilkeyi kapattığınızda, artık hiçbir kullanıcı bu ilke kapsamında lisans talep etmemektedir. Bu değişiklik, bu ilke kapsamında lisans talep eden kullanıcıları etkilemez.

1. Yönetim merkezinde **Faturalama** \> **Lisansları** sayfasına gidin ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">otomatik talep ilkesi</a> sekmesini seçin.
2. Düzenlemek istediğiniz ilkeyi seçin.
3. Ayrıntılar bölmesinde, **Bu ilkeyi aç veya kapat'ın** altında onay kutusunu seçin veya temizleyin.
4. Ayrıntılar bölmesini kapatmak için **Kaydet'i** seçin.

## <a name="edit-the-policy-friendly-name"></a>İlke kolay adını düzenleme

1. Yönetim merkezinde **Faturalama** \> **Lisansları** sayfasına gidin ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">otomatik talep ilkesi</a> sekmesini seçin.
2. Düzenlemek istediğiniz ilkeyi seçin.
3. Ayrıntılar bölmesindeki **İlke adı** bölümünde **Düzenle'yi** seçin.
4. Yeni bir ilke adı girin ve **Kaydet'i** seçin.
5. Ayrıntılar bölmesini kapatmak için **Kaydet'i** seçin.

## <a name="add-or-remove-backup-products"></a>Yedekleme ürünleri ekleme veya kaldırma

İlke oluşturduğunuzda, ilkeye bir ürün eklersiniz. Lisanslar daha sonra bu lisans havuzundan kullanıcılara otomatik olarak atanır. Otomatik talep ilkesi için ürünleri istediğiniz zaman ekleyebilir veya kaldırabilirsiniz. İlkeyle ilişkilendirilmiş bir ürününüz zaten varsa, eklediğiniz tüm ürünler yedekleme ürünleri olarak kabul edilir. İlk üründeki kullanılabilir lisans sayısı kullanıldığında, ilke lisans atamak için listedeki bir sonraki yedekleme ürününü kullanır. [Ürün listesini istediğiniz gibi yeniden sıralayabilirsiniz](#change-the-assigning-apps-and-services).

Yedek bir ürünü kaldırdığınızda, artık lisans atamak için kullanılmaz. Mevcut lisansı olan kullanıcılar bu lisansa sahip olmaya devam eder, ancak yeni kullanıcılar bu ürün için lisans alamaz.

> [!NOTE]
> Otomatik talep ilkesi en az bir ürün içermelidir. İlkedeki tüm ürünleri kaldıramazsınız. Belirli bir otomatik talep ilkesinden lisans atamak istemiyorsanız, [ilkeyi kapatın](#view-an-auto-claim-policy-report).

### <a name="add-a-backup-product"></a>Yedek ürün ekleme

1. Yönetim merkezinde **Faturalama** \> **Lisansları** sayfasına gidin ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">otomatik talep ilkesi</a> sekmesini seçin.
2. Düzenlemek istediğiniz ilkeyi seçin.
3. Ayrıntılar bölmesinde, en alttaki **Bu ilkeye yedek ürün ekle'yi** seçin.
    > [!NOTE]
    > Bu bağlantıyı görmüyorsanız, bunun nedeni hesabınızla ilişkilendirilmiş yalnızca bir ürününüzün olmasıdır.
4. **Ürün ekle** bölmesinde, ilkeye eklenecek ürünü seçmek için açılan listeyi kullanın ve **ardından Ekle'yi** seçin.
5. Ayrıntılar bölmesini kapatmak için **Kaydet'i** seçin.

### <a name="remove-a-backup-product"></a>Yedek ürünü kaldırma

1. Yönetim merkezinde **Faturalama** \> **Lisansları** sayfasına gidin ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">otomatik talep ilkesi</a> sekmesini seçin.
2. Düzenlemek istediğiniz ilkeyi seçin.
3. Ayrıntılar bölmesinde, alt kısımda **Ürünü kaldır'ı** seçin.
4. **İlkeden ürün kaldır** bölmesinde, kaldırmak istediğiniz ilkenin kutusunu seçin ve ardından **Kaydet'i** seçin.
5. Ayrıntılar bölmesini kapatın.

## <a name="change-the-assigning-apps-and-services"></a>Uygulama ve hizmet atamayı değiştirme

Her ürünle ilişkilendirilmiş bir uygulama ve hizmet koleksiyonu vardır. Otomatik talep ilkenizdeki her ürün için, kullanıcıya otomatik olarak bir lisans atandığında hangi uygulama ve hizmetlerin dahil edileceğini belirtebilirsiniz.

1. Yönetim merkezinde **Faturalama** \> **Lisansları** sayfasına gidin ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">otomatik talep ilkesi</a> sekmesini seçin.
2. Düzenlemek istediğiniz ilkeyi seçin.
3. Ayrıntılar bölmesindeki **Uygulamalar ve hizmetler'in** altında **Düzenle'yi** seçin.
4. **Uygulamalar ve hizmetler** bölmesindeki **Ürün** açılan listesinden tek bir ürün seçin veya **Tüm ürünler'i** seçin.
5. Kullanıcıların erişmesini veya erişiminin olmamasını istediğiniz uygulama ve hizmetlerin kutularını işaretleyin veya temizleyin.
6. İşiniz bittiğinde **Kaydet'i** seçin ve ayrıntılar bölmesini kapatın.

## <a name="change-the-assigning-order-for-backup-products"></a>Yedekleme ürünleri için atama sırasını değiştirme

İlkeye atanmış yedek ürünleriniz varsa, kullanıcılar uygulamada oturum açtıklarında lisans atamak için kullanıldıkları sırayı değiştirebilirsiniz.

1. Yönetim merkezinde **Faturalama** \> **Lisansları** sayfasına gidin ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">otomatik talep ilkesi</a> sekmesini seçin.
2. Düzenlemek istediğiniz ilkeyi seçin.
3. Ayrıntılar bölmesindeki **Ürün lisansları** bölümünde, taşımak istediğiniz ürünün yanındaki kutuyu seçin, ardından **Yukarı taşı** veya **Aşağı taşı'yı** seçin.
4. Yeniden sıralamak istediğiniz her ürün için 3. adımı yineleyin.
5. Ürünleri yeniden sıralamayı bitirdiğinizde, Ayrıntılar bölmesini kapatmak için **Kaydet'i** seçin.

## <a name="view-an-auto-claim-policy-report"></a>Otomatik talep ilkesi raporunu görüntüleme

1. Yönetim merkezinde **Faturalama** \> **Lisansları** sayfasına gidin ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2134398" target="_blank">otomatik talep ilkesi</a> sekmesini seçin.
2. **Raporu görüntüle'yi** seçin. **Otomatik talep ilkesi rapor** sayfası, son 90 gün içinde her ilkeden atanan tüm lisansları listeler. Varsayılan olarak, sayfada son 90 gün gösterilir.
3. Gösterilen süreyi değiştirmek için **Son 30 gün** açılan listesini seçin. Son 1, 7, 30 ve 90 güne ilişkin raporları görüntüleyebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Oluşturduğunuz ilkeler altında lisans talep eden kullanıcıların listesini görmek için otomatik **talep ilkesi** sekmesine düzenli aralıklarla dönebilirsiniz.

## <a name="related-content"></a>İlgili içerik

[Kullanıcılara lisans atama](../../admin/manage/assign-licenses-to-users.md) (makale)\
[Abonelik lisanslarını satın alma veya kaldırma](buy-licenses.md) (makale)\
[Abonelikleri ve lisansları anlama](subscriptions-and-licenses.md) (makale)
