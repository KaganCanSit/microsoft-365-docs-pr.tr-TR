---
title: Microsoft 365 Lighthouse'daki Windows 365 (Bulut Bilgisayarlar) sayfasına genel bakış
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Microsoft 365 Lighthouse kullanan Yönetilen Hizmet Sağlayıcıları (MSP) için Windows 365 (Bulut bilgisayarları) sayfası hakkında bilgi edinin.
ms.openlocfilehash: 843e241c796d626ecca2180b0bce1372059701a2
ms.sourcegitcommit: 339d2c2ffea06726f69429f73c1113c649f37b18
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2022
ms.locfileid: "65022899"
---
# <a name="overview-of-the-windows-365-cloud-pcs-page-in-microsoft-365-lighthouse"></a>Microsoft 365 Lighthouse'daki Windows 365 (Bulut Bilgisayarlar) sayfasına genel bakış  
  
Windows 365, Microsoft Endpoint Manager (MEM) yöneticilerinin Windows 365 lisansına sahip kullanıcıları için Bulut bilgisayarları sağlamasına ve yönetmesine olanak tanıyan bulut tabanlı bir hizmettir. Windows 365, cihaz yönetimi için MEM ile ve tüm müşteri kiracılarında Bulut bilgisayarların iş ortağı yönetimine yönelik Microsoft 365 Lighthouse ile tamamen tümleşiktir.

Windows 365 hakkında daha fazla bilgi için bkz[. Windows 365 nedir?](/windows-365/overview) Windows 365 gereksinimlerinin listesi için bkz[. Windows 365 gereksinimleri](/windows-365/enterprise/requirements).

> [!IMPORTANT]
> Lighthouse'da yönetebilmeniz için önce her müşteri kiracısı için Bulut bilgisayarları sağlamak için [MEM'e](https://go.microsoft.com/fwlink/p/?linkid=2150463) gitmeniz gerekir. Lighthouse'un içinden sağlayamazsınız.

Müşteri kiracınız için Bulut bilgisayarları sağladıktan sonra, Microsoft 365 Giriş sayfasındaki Windows 365 kartı, sağlanması başarısız olan Bulut bilgisayarlarının sayısı ve Azure ağ bağlantısı hataları gibi eyleme ihtiyacı olan Bulut bilgisayarları hakkında kısa bir uyarı sağlar. Ayrıntılı bir durum elde etmek için Windows 365 kartındaki düğmeyi seçin (veya sol gezinti bölmesinde **Windows 365** seçin) ve Windows 365 sayfasını açın. Bu sayfadan, müşteri kiracılarınıza atanan Bulut bilgisayarlarının durum genel bakışını alabilir, yönettiğiniz tüm Bulut bilgisayarlarının ve bunların atandığı kiracıların listesini görüntüleyebilir ve müşteri kiracılarınızla Azure Active Directory (Azure AD) arasındaki Azure ağ bağlantılarını ve bunların durumunu görüntüleyebilirsiniz.

## <a name="overview-tab"></a>Genel Bakış sekmesi

Genel Bakış sekmesinde, renkli count-annotation çubuğu aşağıdaki durumlara sahip tüm müşteri kiracılarınız genelinde bulut bilgisayarlarının veya Azure ağ bağlantılarının toplam sayısını görüntüler: Başarısız ağ bağlantıları, Sağlanmadı, Sağlama başarısız oldu ve Sağlama yakında kaldırıldı.

Ek açıklama çubuğunun altındaki listede her müşteri kiracısı için Bulut Bilgisayarı durumlarının dökümünü görebilirsiniz. Hangi kiracıların belirli bir duruma sahip Bulut bilgisayarlarına sahip olduğunu görmek için, listeyi filtrelemek için count-annotation çubuğundan bu durumu seçin. Bir veya daha fazla belirli müşteri kiracısının Bulut Bilgisayar durumlarını görmek için, Listeyi filtrelemek için **Kiracılar** açılan menüsünü kullanın.

Belirli bir müşteri kiracısının ayrıntılı durum bilgilerini almak için, söz konusu kiracının durum sütunlarından herhangi birinin altında bir değer seçin. Değerin hangi sütunda olduğuna bağlı olarak **Azure ağ bağlantıları** veya **Tüm bulut bilgisayarları** sekmesi açılır ve daha fazla bilgi gösterilir.

Genel Bakış sekmesi aşağıdaki seçenekleri de içerir:

- **Yenileme:** En güncel Cloud PC verilerini almak için öğesini seçin.
- **Ihracat:** Cloud PC verilerini virgülle ayrılmış Excel değerler (.csv) dosyasına dışarı aktarmak için seçin.
- **Arama:** Listede belirli bir Bulut bilgisayarı hızla bulmak için anahtar sözcükler girin.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/win365-overview-tab.png" alt-text="Windows 365 Genel Bakış sekmesinin ekran görüntüsü." lightbox="../media/m365-lighthouse-win365-page-overview/win365-overview-tab.png":::

## <a name="all-cloud-pcs-tab"></a>Tüm Bulut Bilgisayarları sekmesi

Tüm Bulut Bilgisayarları sekmesinde, renkli count-annotation çubuğu tüm müşteri kiracılarınızda şu durumlara sahip bulut bilgisayarlarının toplam sayısını görüntüler: Sağlandı, Sağlanmadı, Sağlama başarısız oldu ve Sağlama yakında kaldırıldı.

Tüm Bulut bilgisayarlarını ve sağlama durumlarını ek açıklama çubuğunun altındaki listede görüntüleyebilirsiniz. Aşağıdaki bilgiler sağlanır:

- **Bulut bilgisayar adı:** Bulut bilgisayara atanan ad.
- **Kiracı:** Bulut bilgisayarın sağlandığı müşteri kiracısı.
- **Cihaz adı:** Intune cihaz adı; Bulut bilgisayarın benzersiz tanımlayıcısı.
- **Bilgisayar türü:** Standart SKU'lara göre Bulut bilgisayar türü.
- **Durum:** Bulut bilgisayarın sağlama durumu.
- **Kullanıcı:** Bulut bilgisayarının sağlandığı veya sağlanmaya çalışıldığı kullanıcı.

Hangi kiracıların belirli bir sağlama durumuna sahip Bulut bilgisayarlarına sahip olduğunu görmek için, listeyi filtrelemek için count-annotation çubuğundan bu durumu seçin. Bir veya daha fazla belirli müşteri kiracısının Bulut Bilgisayar sağlama durumlarını görmek için **Kiracılar** açılan menüsünü kullanarak listeyi filtreleyin.

Daha fazla ayrıntı görüntülemek için listeden herhangi bir Cloud PC'yi seçin. Bulut bilgisayarda işlem yapmanız gerekiyorsa, kiracı sağlama ilkelerini ve cihaz ayrıntılarını Microsoft Endpoint Manager görüntüleme seçenekleri vardır.

Tüm Bulut Bilgisayarları sekmesi aşağıdaki seçenekleri de içerir:

- **Yenileme:** En güncel Cloud PC verilerini almak için öğesini seçin.
- **Ihracat:** Cloud PC verilerini virgülle ayrılmış Excel değerler (.csv) dosyasına dışarı aktarmak için seçin.
- **Arama:** Listede belirli bir Bulut bilgisayarı hızla bulmak için anahtar sözcükler girin.
- **Sağlamayı yeniden deneyin:** **Sağlama başarısız** durumundaki listeden 1 ila 20 Bulut bilgisayarı seçin ve ardından bu Bulut bilgisayarları için sağlamayı yeniden denemek için bu seçeneği belirleyin.

Bulut bilgisayar sağlama durumlarının tam listesini ve bunların ne anlama olduğunu görmek için Windows 365 belge kitaplığındaki [Bulut bilgisayarlar için cihaz yönetimine genel bakış](/windows-365/enterprise/device-management-overview#column-details) bölümüne bakın.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/all-cloud-pcs-tab.png" alt-text="Windows 365 Tüm Bulut Bilgisayarları sekmesinin ekran görüntüsü." lightbox="../media/m365-lighthouse-win365-page-overview/all-cloud-pcs-tab.png":::

## <a name="azure-network-connections-tab"></a>Azure ağ bağlantıları sekmesi

Azure ağ bağlantıları sekmesindeki renkli count-annotation çubuğu, tüm müşteri kiracılarınız genelinde aşağıdaki durumlara sahip azure ağ bağlantılarının toplam sayısını görüntüler: Başarılı bağlantılar ve Başarısız bağlantılar.

Ek açıklama ekleme çubuğunun altındaki listede tüm Azure ağ bağlantılarını ve bunların bağlantı durumunu görüntüleyebilirsiniz.

Belirli bir sağlama durumuna sahip bağlantıları görmek için, listeyi filtrelemek için count-annotation çubuğundan bu durumu seçin. Belirli bir veya daha fazla müşteri kiracısının bağlantı durumlarını görmek için **Kiracılar** açılan menüsünü kullanarak listeyi filtreleyin.

Listede bir işlem yapmanız veya bağlantı sorunlarını gidermeniz gerekiyorsa **, Microsoft Endpoint Manager bağlantı ayrıntılarını görüntüle'yi** seçin.

Azure ağ bağlantıları sekmesi aşağıdaki seçenekleri de içerir:

- **Yenileme:** En güncel bağlantı verilerini almak için öğesini seçin.
- **Ihracat:** Bağlantı verilerini virgülle ayrılmış Excel değerler (.csv) dosyasına aktarmak için seçin.
- **Arama:** Belirli bir bağlantıyı hızla bulmak için anahtar sözcükler girin.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/azure-network-connections-tab.png" alt-text="Azure ağ bağlantıları sekmesinin ekran görüntüsü." lightbox="../media/m365-lighthouse-win365-page-overview/azure-network-connections-tab.png":::

## <a name="related-content"></a>İlgili içerik

[Windows 365 nedir?](/windows-365/overview) (makale)\
[Bulut bilgisayarlar için Windows 365 cihaz yönetimine genel bakış](/windows-365/enterprise/device-management-overview) (makale)\
[Microsoft 365 Lighthouse SSS](m365-lighthouse-faq.yml) (makale)