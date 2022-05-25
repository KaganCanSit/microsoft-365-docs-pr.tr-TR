---
title: Self servis satın almaları yönetme (Yöneticiler)
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: prlachhw, pablom
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_ssp
- AdminSurgePortfolio
- okr_smb
search.appverid:
- MET150
description: Yöneticiler, kuruluşlarındaki kullanıcılar tarafından yapılan self servis satın alma işlemlerini yönetmeyi öğrenebilir.
ms.date: 05/24/2022
ms.openlocfilehash: 50d782052839c099f3c64e45cc82a6f2ae5ba853
ms.sourcegitcommit: 612ce4d15d8a2fdbf7795393b50af477d81b6139
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65663524"
---
# <a name="manage-self-service-purchases-admin"></a>Self servis satın almaları yönetme (Yönetici)

Yönetici olarak, kuruluşunuzdaki kişiler tarafından yapılan self servis satın almaları görebilirsiniz. Her self servis satın alma işlemi için ürün adını, satın alan adını, satın alınan abonelikleri, son kullanma tarihini, satın alma fiyatını ve atanan kullanıcıları görürsünüz. Kuruluşunuz için gerekliyse, PowerShell aracılığıyla ürün başına self servis satın almayı kapatabilirsiniz. Self servis satın alma yoluyla veya merkezi olarak satın alınan ürünler üzerinde aynı veri yönetimi ve erişim ilkelerine sahipsiniz.

Ayrıca kuruluşunuzdaki kullanıcıların self servis satın alma işlemi yapıp yapamayacağını da denetleyebilirsiniz. Daha fazla bilgi için bkz. [MSCommerce PowerShell modülü için AllowSelfServicePurchase kullanma](allowselfservicepurchase-powershell.md).

## <a name="view-self-service-subscriptions"></a>Self servis abonelikleri görüntüleme

::: moniker range="o365-worldwide"

1. Yönetim merkezinde **Faturalama** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Ürünleriniz</a> sayfasına gidin.

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetim merkezinde **Faturalama** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">Ürünleriniz</a> sayfasına gidin.
::: moniker-end

2. **Ürünler** sekmesinde filtre simgesini ve ardından **Self servis'i** seçin.
3. Abonelikle ilgili diğer ayrıntıları görüntülemek için listeden bir tane seçin.

## <a name="view-who-has-licenses-for-a-self-service-purchase-subscription"></a>Self servis satın alma aboneliği için kimin lisansı olduğunu görüntüleme

> [!NOTE]
> Yönetici olarak, kuruluşunuzdaki bir kullanıcı tarafından satın alınan self servis satın alma aboneliği için lisans atayamaz veya lisansı kaldıramazsınız. [Self servis satın alma aboneliğini devralabilir](#take-over-a-self-service-purchase-subscription) ve lisansları atayabilir veya atamasını kaldırabilirsiniz.

::: moniker range="o365-worldwide"

1. Yönetim merkezinde **Faturalama** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Lisansları</a> sayfasına gidin.

::: moniker-end

::: moniker range="o365-21vianet"

 1. Yönetim merkezinde **Faturalama** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank">Lisansları</a> sayfasına gidin.

::: moniker-end

2. Filtre simgesini ve ardından **Self servis'i** seçin.
3. Kişilere atanan lisansları görmek için bir ürün seçin.
    > [!NOTE]
    > Bir ürün için birden çok satın alma işlemi varsa, bu ürün yalnızca bir kez listelenir ve **Kullanılabilir miktar** sütunu söz konusu ürün için satın alınan tüm aboneliklerin toplamını gösterir.
4. **Kullanıcılar** listesi, self servis satın alma işlemi yapan kişilerin adlarına göre gruplandırılır.
5. Bu aboneliklerin lisanslarına sahip kullanıcıların listesini dışarı aktarmak için, dışarı aktarmak istediğiniz abonelikleri seçin ve ardından **Kullanıcıları dışarı aktar'ı** seçin.

## <a name="disable-or-enable-self-service-purchases"></a>Self servis satın almaları devre dışı bırakma veya etkinleştirme

Kuruluşunuzdaki kullanıcılar için self servis satın almaları devre dışı bırakabilir veya etkinleştirebilirsiniz. **MSCommerce** PowerShell modülü **AllowSelfServicePurchase** için, kuruluşunuzdaki kullanıcıların self servis satın alıp alamayacağını ve hangi ürünler için satın alabileceğini denetlemenize olanak tanıyan bir **PolicyID** parametre değeri içerir.

**MSCommerce** PowerShell modülünü kullanarak şunları yapabilirsiniz:

- **AllowSelfServicePurchase** parametre değerinin varsayılan durumunu (ürün tarafından etkinleştirildiğinde veya devre dışı bırakılmıştır) görüntüleyin
- Geçerli ürünlerin listesini ve self servis satın alma özelliğinin etkinleştirilip etkinleştirilmediğini görüntüleme
- Belirli bir ürünü etkinleştirmek veya devre dışı bırakmak için geçerli ayarı görüntüleme veya değiştirme

> [!IMPORTANT]
> **AllowSelfServicePurchase** ilkesini kullandığınızda, hem self servis satın almaları hem de self servis denemelerini etkinleştirir veya devre dışı bırakır. Self servis satın alma için kullanılabilen ürünlerin listesi için bkz. [Self servis satın alma ürünlerinin listesini ve durumlarını görüntüleme](allowselfservicepurchase-powershell.md#view-a-list-of-self-service-purchase-products-and-their-status). Deneme aboneliklerinde yalnızca Project ve Visio kullanılabilir.

Daha fazla bilgi için bkz. [MSCommerce PowerShell modülü için AllowSelfServicePurchase kullanma](allowselfservicepurchase-powershell.md).

## <a name="centralize-licenses-under-a-single-subscription"></a>Lisansları tek bir abonelik altında merkezileştirme

Self servis satın alma işlemlerine atanan kullanıcılar için mevcut sözleşmeler aracılığıyla mevcut lisansları atayabilir veya ek abonelik satın alabilirsiniz. Bu merkezi olarak satın alınan lisansları atadıktan sonra, satın alan kişilerin mevcut aboneliklerini iptal etmelerini isteyebilirsiniz.

::: moniker range="o365-worldwide"

1. Yönetim merkezinde **Faturalama** > <a href="https://go.microsoft.com/fwlink/p/?linkid=868433" target="_blank">Satın Alma hizmetleri</a> sayfasına gidin.

::: moniker-end

::: moniker range="o365-21vianet"

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Yönetim merkezinde</a> **Faturalama** > **Satın Alma hizmetleri** sayfasına gidin.

::: moniker-end

2. Satın almak istediğiniz ürünü bulun ve seçin, ardından **Satın Al'ı** seçin.
3. Satın alma işleminizi tamamlamak için kalan adımları tamamlayın.
4. Sonraki adımda başvuracak kullanıcı listesini dışarı aktarmak [için Self servis satın alınan bir abonelik için kimin lisansları olduğunu görüntüleme](#view-who-has-licenses-for-a-self-service-purchase-subscription) bölümündeki adımları izleyin.
5. Diğer abonelikte lisansı olan herkese lisans atayın. Tam adımlar için bkz. [Kullanıcılara lisans atama](../../admin/manage/assign-licenses-to-users.md).
6. Self servis satın alma aboneliğini satın alan kişiye başvurun ve [aboneliği iptal](manage-self-service-purchases-users.md#cancel-a-subscription) etmesini isteyin.

## <a name="take-over-a-self-service-purchase-subscription"></a>Self servis satın alma aboneliğini devralma

Kuruluşunuzdaki bir kullanıcı tarafından yapılan self servis satın alma aboneliğini devralabilirsiniz. Self servis satın alma aboneliğini devraldığınızda iki seçeneğiniz vardır:

1. Kullanıcıları farklı bir aboneliğe taşıyın ve özgün aboneliği iptal edin.
2. Self servis satın alma aboneliğini iptal edin ve atanan kullanıcılardan lisansları kaldırın.

### <a name="move-users-to-a-different-subscription"></a>Kullanıcıları farklı bir aboneliğe taşıma

Kullanıcıları farklı bir aboneliğe taşıdığınızda, eski abonelik otomatik olarak iptal edilir. Self servis satın alma aboneliğini ilk satın alan kullanıcı, aboneliğin iptal edildiğine ilişkin bir e-posta alır.

> [!NOTE]
> Kullanıcıları taşıdığınız abonelikte taşıdığınız her kullanıcı için kullanılabilir bir lisansa sahip olmanız gerekir.

::: moniker range="o365-worldwide"

1. Yönetim merkezinde **Faturalama** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Ürünleriniz</a> sayfasına gidin.

::: moniker-end

::: moniker range="o365-21vianet"

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Yönetim merkezinde</a> **Ürünlerinizi** **Faturalama** > sayfasına gidin.

::: moniker-end

2. **Ürünler** sekmesinde filtre simgesini ve ardından **Self servis'i** seçin.
3. Devralmak istediğiniz aboneliği seçin.
4. Abonelik ayrıntıları sayfasındaki **Abonelikler ve ayarlar** bölümünde **Bu aboneliğin denetimini al'ı** seçin.
5. Sağ bölmede **Kullanıcıları taşı'yı** seçin.
6. Kullanıcıları taşımak istediğiniz ürünü seçin ve ardından **Kullanıcıları taşı'yı** seçin.
7. **Kullanıcıları şuraya taşı** kutusunda Kullanıcıları **taşı'yı** seçin. Taşıma işlemi birkaç dakika sürebilir. İşlem çalışırken tarayıcınızı kapatmayın.
8. Taşıma işlemi tamamlandığında, **Tamamlananları taşı bölmesini** kapatın.
9. Abonelik ayrıntıları sayfasında, self servis satın alınan aboneliğin **Abonelik durumu** **Silinmiş** olarak gösterilir.

### <a name="cancel-a-self-service-purchase-subscription"></a>Self servis satın alma aboneliğini iptal etme

Self servis satın alma aboneliğini iptal etmeyi seçtiğinizde, lisansı olan kullanıcılar ürüne erişimi kaybeder. Self servis satın alma aboneliğini ilk satın alan kullanıcı, aboneliğin iptal edildiğine ilişkin bir e-posta alır.

::: moniker range="o365-worldwide"

1. Yönetim merkezinde **Faturalama** > <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Ürünleriniz</a> sayfasına gidin.

::: moniker-end

::: moniker range="o365-21vianet"

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">Yönetim merkezinde</a> **Ürünlerinizi** **Faturalama** > sayfasına gidin.

::: moniker-end

2. **Ürünler** sekmesinde filtre simgesini ve ardından **Self servis'i** seçin.
3. İptal etmek istediğiniz aboneliği seçin.
4. Abonelik ayrıntıları sayfasındaki **Abonelikler ve ayarlar** bölümünde **Bu aboneliğin denetimini al'ı** seçin.
5. Sağ bölmede **Aboneliği iptal et'i** seçin.
6. Açılan listeden iptaliniz için bir neden seçin ve ardından **Aboneliği iptal et'i** seçin.
7. **İptal etmek istediğinizden emin misiniz?** kutusunda **Aboneliği iptal et'i** seçin.
8. Sağ bölmeyi kapatın.
9. Abonelik ayrıntıları sayfasında **Abonelik durumu** **Silinmiş** olarak gösterilir.

## <a name="need-help-contact-us"></a>Yardıma mı ihtiyacınız var? Bize ulaşın.

Self servis satın almalarla ilgili sık sorulan sorular için bkz. [Self servis satın almalar hakkında SSS](self-service-purchase-faq.yml).

Self servis satın alma işlemleriyle ilgili sorularınız veya yardıma ihtiyacınız varsa [desteğe başvurun](../../admin/get-help-support.md).
