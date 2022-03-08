---
title: Self servis satın almaları yönetme (Yöneticiler)
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: mijeffer, pablom
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
description: Yöneticiler, kuruluşlarına kullanıcılar tarafından yapılan self servis satın almaları yönetmeyi öğrenebilir.
ms.date: 03/26/2021
ms.openlocfilehash: 19f276107de7b1dd1053e500d249950a8700ac41
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63319735"
---
# <a name="manage-self-service-purchases-admin"></a>Self servis satın almaları yönetme (Yönetici)

Yönetici olarak, kurum içinde yer alan kişilerin yaptığı self servis satın almaları görebilirler. Her self servis satın alma için ürün adını, satın almacı adını, satın alınan abonelikleri, son kullanma tarihini, satın alma fiyatını ve atanan kullanıcıları görüyorsunuz. Kuruluş için gerekirse, PowerShell aracılığıyla self servis satın almaları ürün başına kapatabilirsiniz. Self servis satın alma yoluyla veya merkezi olarak satın alınan ürünler üzerinde aynı veri yönetimi ve erişim ilkelerine sahipsiniz.

Ayrıca, kurumuz kullanıcıların self servis satın almalar edip edip etmey denetlemeniz de gerekir. Daha fazla bilgi için bkz [. MSCommerce PowerShell modülü için AllowSelfServicePurchase kullanma](allowselfservicepurchase-powershell.md).

## <a name="view-self-service-subscriptions"></a>Self servis abonelikleri görüntüleme

::: moniker range="o365-worldwide"

1. Yönetim merkezinde Ürünlerinizi Faturalandırma **sayfasına** > gidin.<a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank"></a>

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetim merkezinde Ürünlerinizi Faturalandırma **sayfasına** \> gidin.<a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank"></a>
::: moniker-end

2. Ürünler **sekmesinde filtre** simgesini seçin ve ardından Self **servis'i seçin**.
3. Abonelikle ilgili daha fazla ayrıntı görüntülemek için listeden bir abonelik seçin.

## <a name="view-who-has-licenses-for-a-self-service-purchase-subscription"></a>Self servis satın alma aboneliği için kimin lisansı olduğunu görüntüleme

> [!NOTE]
> Yönetici olarak, kurumda bir kullanıcı tarafından satın alınan self servis satın alma aboneliği için lisans atayayam veya atamalarını iptal edilemez. Self [servis satın alma aboneliğini üzerine alıp](#take-over-a-self-service-purchase-subscription) lisansları atayın veya atamalarını iptal edin.

::: moniker range="o365-worldwide"

1. Yönetim merkezinde Fatura Lisansları **sayfasına** > gidin.<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank"></a>

::: moniker-end

::: moniker range="o365-21vianet"

 1. Yönetim merkezinde Fatura Lisansları **sayfasına** \> gidin.<a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank"></a>

::: moniker-end

2. Filtre simgesini seçin ve sonra Self **servis'i seçin**.
3. İnsanlara atanan lisansları görmek için bir ürün seçin.
    > [!NOTE]
    > Bir ürün için birden çok satın alma varsa, bu ürün yalnızca bir kez listelenir ve Kullanılabilir miktar sütununda  bu ürün için satın alınan tüm aboneliklerin toplamı gösterilir.
4. Kullanıcılar **listesi** , self servis satın alma yapan kişilerin adlara göre gruptır.
5. Bu aboneliklerin lisansları olan kullanıcıların listesini dışarı aktarmak için, dışarı aktarmak istediğiniz abonelikleri ve sonra Kullanıcıları dışarı **aktar'ı seçin**.

## <a name="disable-or-enable-self-service-purchases"></a>Self servis satın almaları devre dışı bırakma veya etkinleştirme

Kurum daki kullanıcılar için self servis satın almaları devre dışı bırakabilirsiniz veya etkinleştirebilirsiniz. **MSCommerce** PowerShell modülü, **AllowSelfServicePurchase** için bir **PolicyID** parametre değeri içerir ve bu değer, kurumdaki kullanıcıların self servis satın almalar yapma ve hangi ürünler için self servis alışveriş yapma olanaklarını denetlemenize olanak sağlar.

**MSCommerce PowerShell modülünü** kullanarak şunları yapmak için kullanabilirsiniz:

- Ürün tarafından etkinleştirildiğinde veya devre dışı bırakildiğinde **, AllowSelfServicePurchase** parametre değerinin varsayılan durumunu görüntüleme
- Geçerli ürünlerin listesini ve self servis alışverişin etkinleştirildiğinde veya devre dışı bırakılmıştır
- Belirli bir ürünü etkinleştirmek veya devre dışı bırakmak için geçerli ayarı görüntüleme veya değiştirme

Daha fazla bilgi için bkz [. MSCommerce PowerShell modülü için AllowSelfServicePurchase kullanma](allowselfservicepurchase-powershell.md).

## <a name="centralize-licenses-under-a-single-subscription"></a>Tek bir abonelik altındaki lisansları merkezileştirme

Self servis satın alma işlemlerine atanan kullanıcılar için mevcut lisansları ataabilir veya mevcut sözleşmeler aracılığıyla ek abonelik satın alabilirsiniz. Bu merkezi olarak satın alınan lisansları atadikten sonra, satın almacılardan mevcut aboneliklerini iptal etmelerini talep edebilirsiniz.

::: moniker range="o365-worldwide"

1. Yönetim merkezinde Fatura Satın Alma **hizmetleri** > <a href="https://go.microsoft.com/fwlink/p/?linkid=868433" target="_blank">sayfasına</a> gidin.

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetim <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">merkezinde Faturalama</a> Satın Alma **hizmetleri** > **sayfasına** gidin.

::: moniker-end

2. Satın almak istediğiniz ürünü bulup seçin ve sonra Satın Al'ı **seçin**.
3. Satın alma işleminizi tamamlamak için kalan adımları tamamlayın.
4. Bir sonraki adımda [, self servis satın alınan](#view-who-has-licenses-for-a-self-service-purchase-subscription) abonelik için kimlerin lisansı olduğunu görüntüleme altında yer alan adımları izleyin ve bir kullanıcı listesini dışarı aktarın.
5. Diğer abonelikte lisansı olan herkese lisans attayabilirsiniz. Tam adımlar için bkz. [Kullanıcılara lisans atama](../../admin/manage/assign-licenses-to-users.md).
6. Self servis satın alma aboneliğini satın alan kişiye ulaşın ve aboneliği iptal [etmelerini sorun](manage-self-service-purchases-users.md#cancel-a-subscription).

## <a name="take-over-a-self-service-purchase-subscription"></a>Self servis satın alma aboneliğini alma

Kendi kendine satın alma aboneliğini, kurumda bir kullanıcı tarafından satın alınabilir. Self servis satın alma aboneliğini üzerine aldığınız zaman iki seçenek vardır:

1. Kullanıcıları farklı bir aboneliğe taşıma ve ilk aboneliği iptal etme.
2. Self servis satın alma aboneliğini iptal edin ve atanan kullanıcıların lisanslarını kaldırın.

### <a name="move-users-to-a-different-subscription"></a>Kullanıcıları farklı bir aboneliğe taşıma

Kullanıcıları farklı bir aboneliğe taşıyırsınız, eski abonelik otomatik olarak iptal edilir. Başlangıçta self servis satın alma aboneliğini satın alan kullanıcı, aboneliğin iptal edildiğini söyleyen bir e-posta alır.

> [!NOTE]
> Kullanıcılarını taşınmasını istediğiniz abonelikte, her kullanıcı için uygun bir lisansınız olması gerekir.

::: moniker range="o365-worldwide"

1. Yönetim merkezinde Ürünlerinizi Faturalandırma **sayfasına** > gidin.<a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank"></a>

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetim <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">merkezinde Ürünlerinizi</a> Faturalandırma **sayfasına** > gidin.

::: moniker-end

2. Ürünler **sekmesinde filtre** simgesini seçin ve ardından Self **servis'i seçin**.
3. Üzerine almak istediğiniz aboneliği seçin.
4. Abonelik ayrıntıları sayfasında, Abonelikler ve **ayarlar bölümünde** Bu aboneliğin kontrolünü **al'ı seçin**.
5. Sağ bölmede Kullanıcıları **taşı'ya tıklayın**.
6. Kullanıcıları taşımak istediğiniz ürünü seçin ve ardından Kullanıcıları **taşı'ya seçin**.
7. Kullanıcıları taşı **kutusunda Kullanıcıları** **taşı'ya tıklayın**. Taşıma işlemi birkaç dakika sürebilir. İşlem çalışırken tarayıcınızı kapatabilirsiniz.
8. Taşıma işlemi tamamlandığında, Tamamlananları taşı **bölmesini kapatın**.
9. Abonelik ayrıntıları sayfasında, satın **alınan self servis** abonelik için Abonelik durumu Silinmiş olarak **görüntülenir**.

### <a name="cancel-a-self-service-purchase-subscription"></a>Self servis satın alma aboneliğini iptal etme

Self servis satın alma aboneliğini iptal etmek tercih edersiniz, lisansı olan kullanıcılar ürüne erişimi kaybeder. Başlangıçta self servis satın alma aboneliğini satın alan kullanıcı, aboneliğin iptal edildiğini söyleyen bir e-posta alır.

::: moniker range="o365-worldwide"

1. Yönetim merkezinde Ürünlerinizi Faturalandırma **sayfasına** > gidin.<a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank"></a>

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetim <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">merkezinde Ürünlerinizi</a> Faturalandırma **sayfasına** > gidin.

::: moniker-end

2. Ürünler **sekmesinde filtre** simgesini seçin ve ardından Self **servis'i seçin**.
3. İptal etmek istediğiniz aboneliği seçin.
4. Abonelik ayrıntıları sayfasında, Abonelikler ve **ayarlar bölümünde** Bu aboneliğin kontrolünü **al'ı seçin**.
5. Sağ bölmede Aboneliği iptal **et'i seçin**.
6. Açılan listeden iptal işleminizin nedenini seçin, ardından Aboneliği iptal **et'i seçin**.
7. İptal etmek **istediğinizden emin misiniz? kutusunda Aboneliği** iptal **et'i seçin**.
8. Sağ bölmeyi kapatın.
9. Abonelik ayrıntıları sayfasında, Abonelik durumu **Silinmiş olarak** **görüntülenir**.

## <a name="need-help-contact-us"></a>Yardıma mı ihtiyacınız var? Bize ulaşın.

Self servis satın almalar hakkında sık sorulan sorular için bkz. [Self servis satın almalar hakkında SSS](self-service-purchase-faq.yml).

Self servis satın alma ile ilgili sorularınız varsa veya yardıma ihtiyacınız varsa destek [ile iletişime geçin](../../admin/get-help-support.md).
