---
title: Güvenlik için tehdit korumasını Microsoft 365 İş Ekstra
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
description: Veri kaybını önlemek ve müşterinizin hassas bilgilerini güvende tutmaya yardımcı olmak için uyumluluk özelliklerini ayarlayın.
ms.openlocfilehash: baac8bc1ad9a425ad7219a1e76949286858f60e0
ms.sourcegitcommit: 601ab9ad2b624e3b5e04eed927a08884c885c72a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2022
ms.locfileid: "64403787"
---
# <a name="set-up-compliance-features"></a>Uyumluluk özelliklerini ayarlama

Microsoft 365 İş Ekstra aboneliğiniz uyumluluk ve gizlilik özelliklerini içerir. Bu özellikler, şirketinizin verilerini korumaya ve sizin ve müşterilerinize ilişkin hassas bilgileri güvende tutmanıza yardımcı olur. Bu makale, uyumluluk özelliklerinize başlamanıza yardımcı olmak için tasarlanmıştır.

## <a name="before-you-begin"></a>Başlamadan önce

Azure Active Directory'de şu rollerden birinin atanmış olduğundan emin Azure Active Directory:

- Genel Yönetici
- Uyumluluk Yöneticisi

Daha fazla bilgi edinmek için [Kullanmaya başlayın sayfasına bakın](../add-users/admin-roles-page.md).

## <a name="use-compliance-manager-to-get-started"></a>Kullanmaya başlamak için Uyumluluk Yöneticisi'ni kullanma

:::image type="content" source="../../business-premium/media/m365bp-compliancemanager.png" alt-text="Microsoft 365 İş Ekstra'da Uyumluluk Yöneticisi'nin ekran Microsoft 365 İş Ekstra.":::

Microsoft 365 İş Ekstra, uyumluluk özelliklerinizi ayarlamaya başlamanıza yardımcı olan Uyumluluk Yöneticisi'ni içerir. Bu tür özellikler arasında veri kaybını önleme, bilgi idaresi ve insider risk yönetimi yer alan birkaç özellik vardır. Uyumluluk Yöneticisi önerileri, uyumluluk puanını ve puanınızı geliştirme yollarını vurgularken size zaman tasarrufu sağlar.

Şu şekilde başlandı:

1. Gidin ve [https://compliance.microsoft.com](https://compliance.microsoft.com) oturum açma.

2. Gezinti bölmesinde Uyumluluk **Yöneticisi'ni seçin**.

3. Genel Bakış **sekmesinde** bilgileri gözden geçirebilirsiniz. Daha fazla bilgi görüntülemek veya veri kaybı önleme (DLP) ilkesi yapılandırma gibi işlemler yapmak için bir öğe veya bağlantı seçin. Örneğin, **Puanınızı etkileyen çözümler bölümünde** Kalan eylemler sütunundaki **bağlantıyı seçin** .

   :::image type="content" source="../../business-premium/media/m365bp-compliancesolutions.png" alt-text="Puanınızı Etkileyen Çözümlerin ekran görüntüsü.":::

   Bu eylem sizi seçtiğiniz **öğe için** filtrelenmiş geliştirme eylemleri sekmesine alır. Bu örnekte, yapılandırılan DLP ilkelerini arıyoruz.

   :::image type="content" source="../../business-premium/media/m365bp-dlppoliciestoconfigure.png" alt-text="Yapılandırılan DLP ilkelerinin ekran görüntüsü.":::

4. Geliştirme **eylemleri sekmesinde** bir öğeyi seçin. Örneğimizde, Özelleştirilmiş **DLP ilkeleri veya kişisel olarak tanınmayı sağlayacak bilgiler oluştur'i seçtik**. Yapılandırılan ilke hakkında daha fazla bilgi sağlayan bir sayfa yüklenir.

   :::image type="content" source="../../business-premium/media/m365bp-dlppolicyinfo.png" alt-text="Müşteri içeriğine ilişkin DLP ilkesiyle ilgili bilgilerin ekran görüntüsü.":::

   DLP ilkenizi ayarlamak için ekranda bilgileri izleyin.

İşletmeler için uyumluluk özellikleri hakkında daha Microsoft 365 için uyumluluk belgelerini [Microsoft 365 bakın](../../compliance/index.yml).

## <a name="use-sensitivity-labels"></a>Duyarlılık etiketlerini kullanma

Duyarlılık etiketleri Office Outlook Word, Excel gibi PowerPoint. Etiket örnekleri:

- Normal
- Personal
- Özel
- Gizli

Bununla birlikte, şirketin için de başka etiketler tanımlayabilirsiniz.

Duyarlılık etiketleriyle çalışmaya başlamak için aşağıdaki makaleleri kullanın:

1. [Duyarlılık etiketleri nedir?](../../compliance/sensitivity-labels.md)

2. [Kullanmaya başlayın etiketlerinizi oluşturma](../../compliance/get-started-with-sensitivity-labels.md)

3. [Duyarlılık etiketlerini ve ilkelerini yayımlama](../../compliance/create-sensitivity-labels.md)

4. [Şirketideki kişilerin duyarlılık etiketlerini nasıl kullanacaklarını gösterme](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)