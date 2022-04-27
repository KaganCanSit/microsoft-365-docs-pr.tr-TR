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
ms.openlocfilehash: 325fe39c144227052c966b81a8a2109a07fb0cf2
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100291"
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
- **Kullanıcı:** Bulut bilgisayarının sağlandığı veya sağlanmaya çalışıldığı kullanıcı.
- **Cihaz adı:** Intune cihaz adı; Bulut bilgisayarın benzersiz tanımlayıcısı.
- **Kiracı:** Bulut bilgisayarın sağlandığı müşteri kiracısı.
- **Durum:** Bulut bilgisayarın sağlama durumu.
- **Lisans türü:** Enterprise veya İş.
- **Özellikler:** Bulut bilgisayar donanım yapılandırması.

Hangi kiracıların belirli bir sağlama durumuna sahip Bulut bilgisayarlarına sahip olduğunu görmek için, listeyi filtrelemek için count-annotation çubuğundan bu durumu seçin. Bir veya daha fazla belirli müşteri kiracısının Bulut Bilgisayar sağlama durumlarını görmek için **Kiracılar** açılan menüsünü kullanarak listeyi filtreleyin.

Daha fazla ayrıntı görüntülemek ve aşağıdaki gibi yönetim eylemlerini yürütmek için listeden herhangi bir Cloud PC'yi seçin:
- **Yeni -den başlatın:** Cihazı yeniden başlatmak için öğesini seçin. 
- **Yeniden sağlama:** Cihazı sıfırlamak için öğesini seçin. Sağlama ilkesini Microsoft Endpoint Manager bağlantısında da görüntüleyebilirsiniz.
- **Yeni -den adlandırmak:** Kullanıcıya atanan cihazı yeniden adlandırmak için öğesini seçin.

Tüm Bulut Bilgisayarları sekmesi aşağıdaki seçenekleri de içerir:

- **Ihracat:** Cloud PC verilerini virgülle ayrılmış Excel değerler (.csv) dosyasına dışarı aktarmak için seçin.
- **Yenileme:** En güncel Cloud PC verilerini almak için öğesini seçin.
- **Arama:** Listede belirli bir Bulut bilgisayarı hızla bulmak için anahtar sözcükler girin.

Bulut bilgisayar sağlama durumlarının tam listesini ve bunların ne anlama olduğunu görmek için Windows 365 belge kitaplığındaki [Bulut bilgisayarlar için cihaz yönetimine genel bakış](/windows-365/enterprise/device-management-overview#column-details) bölümüne bakın.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/all-cloud-pcs-tab.png" alt-text="Windows 365 Tüm Bulut Bilgisayarları sekmesinin ekran görüntüsü." lightbox="../media/m365-lighthouse-win365-page-overview/all-cloud-pcs-tab.png":::

## <a name="azure-network-connections-tab"></a>Azure ağ bağlantıları sekmesi

Azure ağ bağlantıları sekmesindeki renkli count-annotation çubuğu, Windows 365 Enterprise Bulut bilgisayarlarına sahip olan ve şu durumlara sahip olabilecek tüm müşteri kiracılarınız genelinde toplam Azure ağ bağlantısı sayısını görüntüler: Başarılı bağlantılar ve Başarısız bağlantılar.

Ek açıklama ekleme çubuğunun altındaki listede tüm Azure ağ bağlantılarını ve bunların bağlantı durumunu görüntüleyebilirsiniz.

Belirli bir sağlama durumuna sahip bağlantıları görmek için, listeyi filtrelemek için count-annotation çubuğundan bu durumu seçin. Belirli bir veya daha fazla müşteri kiracısının bağlantı durumlarını görmek için **Kiracılar** açılan menüsünü kullanarak listeyi filtreleyin.

Listede bir işlem yapmanız veya bağlantı sorunlarını gidermeniz gerekiyorsa **, Microsoft Endpoint Manager bağlantı ayrıntılarını görüntüle'yi** seçin.

Azure ağ bağlantıları sekmesi aşağıdaki seçenekleri de içerir:

- **Ihracat:** Bağlantı verilerini virgülle ayrılmış Excel değerler (.csv) dosyasına aktarmak için seçin.
- **Yenileme:** En güncel bağlantı verilerini almak için öğesini seçin.
- **Arama:** Belirli bir bağlantıyı hızla bulmak için anahtar sözcükler girin.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/azure-network-connections-tab.png" alt-text="Azure ağ bağlantıları sekmesinin ekran görüntüsü." lightbox="../media/m365-lighthouse-win365-page-overview/azure-network-connections-tab.png":::

## <a name="related-content"></a>İlgili içerik

[Windows 365 nedir?](/windows-365/overview) (makale)\
[Bulut bilgisayarlar için Windows 365 cihaz yönetimine genel bakış](/windows-365/enterprise/device-management-overview) (makale)\
[Microsoft 365 Lighthouse SSS](m365-lighthouse-faq.yml) (makale)