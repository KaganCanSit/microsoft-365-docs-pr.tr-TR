---
title: Kaynakta Maliyet yönetimini Microsoft 365 yönetim merkezi
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: drjones, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- commerce_subscriptions
- AdminTemplateSet
search.appverid: MET150
description: Kuruluş maliyetlerinizi görüntülemek, çözümlemek ve yönetmek için Microsoft 365 yönetim merkezi yönetim görünümünde maliyet yönetimi özelliğini nasıl kullanabileceğinizi öğrenin.
ms.date: 03/09/2022
ms.openlocfilehash: c0cfcd47e20d34b12af1276995b0c0cfe1dc1ee7
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63705462"
---
# <a name="use-cost-management-in-the-microsoft-365-admin-center"></a>Kaynakta Maliyet yönetimini Microsoft 365 yönetim merkezi

Microsoft Müşteri Sözleşmesi (MCA) olan bir Genel veya Faturalama yöneticisiyseniz, hizmet maliyetlerinizi görüntülemek, çözümlemek ve yönetmek için Microsoft 365 yönetim merkezi sayfasındaki Maliyet yönetimi sayfasını kullanabilirsiniz. Maliyet yönetimi sayfasına **almak için**, yönetim merkezi sol gezinti bölmesinde FaturaKost **yönetimi'ni** >  **seçin**.

## <a name="before-you-begin"></a>Başlamadan önce

Bu makalede açıklanan adımları takip etmek için Genel veya Faturalama yöneticisi olun. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../admin/add-users/about-admin-roles.md).

## <a name="what-is-cost-management"></a>Maliyet yönetimi nedir?

Maliyet yönetimi, bir kuruluşun bütçesini planlamak ve kontrol etmek için kullanılan bir yöntemdir. Microsoft, yalnızca kullanım ücretleri ödey adresiniz olan kullanııla ödeme modeli kullanan yeni ürün ve hizmetleri sunmaktadır. Aşağıdaki Microsoft 365 yönetim merkezi yönetimi özellikleri, kuruluş varlıklarını yönetmek için gereken maliyeti ve yükü azaltmaya ve aynı zamanda değişken ödeme sürelerinizi takip etmeye yardımcı olur. Şunları da yapabilirsiniz:

- Aylık faturanızı oluşturmak için kullanılan maliyet ve kullanım verilerini indirme
- Maliyetlerinize önceden veri çözümlemesi uygulama
- Harcama eşiklerini ayarlama
- Harcamalarınızı en iyi duruma getirmek için iş yükü değişikliklerini belirleme (iç süreçler)

## <a name="understand-your-costs"></a>Maliyetlerinizi anlama

Faturayla ödeme Microsoft 365 gözden geçirmek ve fatura bilgilerine erişimi yönetmek için fatura özellikleri kullanabilirsiniz. Büyük kuruluşlarda, tedarik ve finans ekipleri genellikle fatura görevlerini yerine gösterir.

Microsoft 365'i kullanmak için kaydolsanız bile, sizin için otomatik olarak bir fatura hesabı oluşturulur. Faturalarınızı ve ödemelerinizi yönetmek ve maliyetleri izlemek için fatura hesabını kullanırsınız. Birden çok fatura hesabınız olabilir. Organizasyon için her tüzel kuruluş veya satış adresi için ayrı bir fatura hesabı alırsınız.

## <a name="plan-and-control-costs"></a>Maliyetleri planlama ve denetleme

Aşağıdaki görevleri yerine Microsoft 365 yönetim merkezi maliyet yönetimi, organizasyon maliyetlerinizi planlamanıza ve denetlemenize yardımcı olur:

- **Maliyetleri çözümleme:** Maliyet yönetimi görünümleri, kuruluş maliyetlerinizi incelemenizi ve çözümlemenizi sağlar. Maliyetlerin nereden tahakkuk eden bir bütün olduğunu anlamak ve harcama eğilimlerini tanımlamak için, kuruluşa göre toplu maliyetleri görüntüabilirsiniz. Bir bütçeye göre aylık, üç aylık ve hatta yıllık maliyet eğilimlerini tahmin etmek için, zaman içinde birikimli maliyetleri de görebilirsiniz.
- **Bütçe oluşturma:** Bütçeler, organizasyonda mali sorumluluk planlamanıza ve karşılamanıza yardımcı olur. Maliyet eşiklerinin veya sınırlarının aş geçitlerini önlemeye yardımcı olur. Bütçeler, maliyetleri önceden yönetmek için harcamaları konusunda diğerni bilgilendirmeye de yardımcı olabilir. Bütçelerle de, organizasyonda harcamanın zamanla nasıl ilerler adı olduğunu anabilirsiniz.

## <a name="view-costs"></a>Maliyetleri görüntüleme

Yönetim **merkezinde** Maliyet yönetimi sayfasının bir Hizmetler sekmesi vardır ve  burada bugün kullanmakta olan farklı ürün ve hizmetlerin dökümünü görebilirsiniz.

:::image type="content" source="../media/mac-billing-costmgmt/MAC-Billing-CostMgmt.png" alt-text="Sayfanın Maliyet yönetimi Microsoft 365 yönetim merkezi.":::

Seçilen **dönem** içinde kullanılan tüm hizmetlerin listesini görmek için Hizmetler sekmesini kullanın. Sayfada yer alan grafik, ilk 10 hizmet için maliyetleri günlük olarak kırar. Geçmiş maliyetlerine bakmak için tarih seçiciyi kullanın ve maliyet eğilimlerini karşılaştırmak için farklı tarih aralıkları kullanın.

## <a name="download-costs"></a>İndirme maliyetleri

Günlük **maliyet verilerinizi** CSV veya dosya dosyasına indirmek için İndir'Excel seçin. Gerektiğinde verilerinizi kullanarak ücretlerinizi daha fazla çözüme sahip olabilir veya diğer verilerle birleştirebilirsiniz.

## <a name="create-budgets"></a>Bütçe oluşturma

Bütçeler, ücretlerinizi izlemenizi ve belirli eşikleri aş karşılarken farkında çalışmanızı sağlar. Her ay altında kalmak istediğiniz bir eşik miktarı ayarlay istediğiniz hızlı bir bütçe oluşturabilirsiniz. Maliyetleriniz bu eşiği aştıyken hızlı bütçe size bir bildirim gönderir. Bildirimler yalnızca bütçeyi oluşturan yöneticiye gönderilir.

:::image type="content" source="../media/mac-billing-costmgmt/MAC-Billing-CostMgmt-CreateBudget.png" alt-text="Çalışma penceresinde Bütçe Microsoft 365 yönetim merkezi.":::

Bütçeyi özelleştirmek için Gelişmiş ayarları **yapılandır'ı seçin**. Bütçenize bir ad ve ardından bütçe sıklığını değiştirebilirsiniz. Ayrıca aylık, üç aylık veya yıllık bir bütçe de ayarlanacak ve bütçe bildirimlerinin gönderilecek dönemi seçebilirsiniz.

:::image type="content" source="../media/mac-billing-costmgmt/MAC-Billing-CostMgmt-CreateBudget-Details.png" alt-text="Aşağıdaki pencerede genişletilmiş bütçe Microsoft 365 yönetim merkezi.":::

## <a name="related-content"></a>İlgili içerik

[Maliyet Yönetimi en iyi yöntemleri](/azure/cost-management-billing/costs/cost-mgt-best-practices) (makale)
