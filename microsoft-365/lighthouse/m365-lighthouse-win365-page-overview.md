---
title: Microsoft 365 Lighthouse Windows 365 (Bulut PC) sayfasına genel bakış
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
description: MICROSOFT 365 LIGHTHOUSE kullanan Yönetilen Hizmet Sağlayıcıları (MSP)'ler için, Windows 365 (Bulut PC'ler) sayfası hakkında bilgi edinebilirsiniz.
ms.openlocfilehash: fa910e3de992aa3f3f76090f76a473a96aebc8fb
ms.sourcegitcommit: 9d563faeaa50b59b0b468dbb373d886e5270f58e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2022
ms.locfileid: "64387111"
---
# <a name="windows-365-cloud-pcs-page-overview"></a>Windows 365 (Bulut BILGISAYARLAR) sayfasına genel bakış  
  
Windows 365, bulut tabanlı bir hizmettir ve Microsoft Endpoint Manager (MEM) yöneticilerinin, bulut lisansına sahip olan kullanıcıları için Bulut PC'leri hazırlamasını ve yönetmesini Windows 365 sağlar. Windows 365 yönetimi için MEM ile ve tüm müşteri kiracılarında Bulut pc'lerin iş ortağı yönetimine Microsoft 365 Lighthouse ile tamamen tümleşiktir.

Bu konuda daha fazla Windows 365 için bkz[. Windows 365?](/windows-365/overview) Bu gereksinimlerin listesi Windows 365 için bkz. [Sistem Windows 365](/windows-365/enterprise/requirements).

> [!IMPORTANT]
> Her müşteri kiracısı [için Bulut PC sağlamak için MEM'ye](https://go.microsoft.com/fwlink/p/?linkid=2150463) gidip bu bilgisayarları Deniz Feneri'nde yönetemenizi gerekir. Deniz Feneri'nin dışından sağ şey sağ şey değil.

Müşteri kiracınız için Bulut PC'ler sağlandıktan sonra Microsoft 365 Giriş sayfasındaki Windows 365 kartı, sağlamada başarısız olan Bulut BILGISAYAR sayısı ve Azure ağ bağlantısı hataları gibi, işlem gereken Bulut pc'ler hakkında kısa bir uyarı sağlar. Ayrıntılı durum bilgi almak için, Windows 365 kartının düğmesini seçin (Windows 365 gezinti bölmesindeKimlik düğmesini  seçerek) Windows 365 açın. Bu sayfadan, müşteri kiracılarına atanan Bulut PC'lere ilişkin bir durum genel bakış elde eder, yönetmek istediğiniz tüm Bulut BILGISAYARLARıN ve atandığı kiracıların listesini ekleyebilirsiniz ve müşteri kiracıları ile Azure Active Directory (Azure AD) ve bunların durumu arasındaki Azure ağ bağlantılarını görüntüleyebilirsiniz.

## <a name="overview-tab"></a>Genel Bakış sekmesi

Genel Bakış sekmesindeki renkli ek açıklama çubuğu, aşağıdaki durumlara sahip tüm müşteri kiracılar genelinde Bulut PC'lerin veya Azure ağ bağlantılarının toplam sayısını gösterir: Başarısız ağ bağlantıları, Sağlanamadı, Sağlama başarısız oldu ve Yakında Yeniden Sağlama.

Ek açıklama çubuğunun altındaki listede her müşteri kiracısı için Bulut Bilgisayar durumlarının dökümünü görebilirsiniz. Hangi kiracılarda belirli bir durumda Bulut PC olduğunu görmek için, bu durumu sayma çubuğundan seçerek listeye filtre ekleyin. Belirli bir veya birden çok müşteri kiracısı için Bulut Bilgisayarı'nın durumunu görmek için, **Listeyi filtrelemek** için Kiracılar açılan menüsünü kullanın.

Belirli bir müşteri kiracısına ilişkin ayrıntılı durum bilgilerini almak için, o kiracının durum sütunlarının herhangi biri altında bir değer seçin. Değerin hangi sütunda yer ağına bağlı olarak, **Azure ağ** bağlantıları veya **Tüm bulut PC'ler** sekmesi açılır ve daha fazla bilgi gösterir.

Genel Bakış sekmesi aşağıdaki seçenekleri de içerir:

- **Yenile:** En güncel Bulut Bilgisayar verilerini almak için seçin.
- **Dışarı aktar:** Bulut Bilgisayar verilerini virgülle ayrılmış değerler (Excel) dosyasına dışarı .csv seçin.
- **Arama:** Listede belirli bir Bulut Bilgisayarı'nın yerini hızla bulmak için anahtar sözcükleri girin.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/win365-overview-tab.png" alt-text="Genel Bakış Windows 365 ekran görüntüsü." lightbox="../media/m365-lighthouse-win365-page-overview/win365-overview-tab.png":::

## <a name="all-cloud-pcs-tab"></a>Tüm Bulut Bilgisayarlar sekmesi

Tüm Bulut PC'ler sekmesinde renkli ek açıklama çubuğu, aşağıdaki durumlara sahip tüm müşteri kiracılar genelinde Bulut PC'lerin toplam sayısını görüntüler: Sağlandı, Sağlanamadı, Sağlama başarısız oldu ve Yakında Geri Alma.

Tüm Bulut PC'leri ve bunların hazırlama durumunu ek açıklama çubuğunun altındaki listede görüntüleyebilirsiniz. Aşağıdaki bilgiler sağlanır:

- **Bulut bilgisayar adı:** Bulut bilgisayara atanan ad.
- **Kiracı:** Bir Bulut bilgisayarının sağladığı müşteri kiracısı.
- **Cihaz adı:** Intune adı olan bir Bulut Bilgisayarı için benzersiz tanımlayıcıdır.
- **Bilgisayar türü:** Standart SKUs'a göre Bulut Bilgisayar türü.
- **Durum:** Bulut Bilgisayarı'nın sağlama durumu.
- **Kullanıcı:** Bulut Bilgisayarı sağlandı veya sağlamayı denilen kullanıcı.

Belirli bir sağlama durumuna sahip Bulut bilgisayarların hangi kiracılarda olduğunu görmek için, ek açıklama çubuğundan bu durumu seçerek listeye filtre ekleyin. Belirli bir veya birden çok müşteri kiracısı için Bulut PC sağlama durumlarını görmek için, Listeyi filtrelemek **için** Kiracılar açılan menüsünü kullanın.

Daha fazla ayrıntı görüntülemek için listeden herhangi bir Bulut Bilgisayarı seçin. Bulut PC'de bir işlem yapmak zorundaysanız, mobil cihazda kiracı hazırlama ilkelerini ve cihaz ayrıntılarını görüntüleme Microsoft Endpoint Manager.

Tüm Bulut Pc'ler sekmesi de aşağıdaki seçenekleri içerir:

- **Yenile:** En güncel Bulut Bilgisayar verilerini almak için seçin.
- **Dışarı aktar:** Bulut Bilgisayar verilerini virgülle ayrılmış değerler (Excel) dosyasına dışarı .csv seçin.
- **Arama:** Listede belirli bir Bulut Bilgisayarı'nın yerini hızla bulmak için anahtar sözcükleri girin.
- **Sağlamayı yeniden deneyin:** Listeden Sağlama başarısız durumuna sahip 1 - 20 Bulut BILGISAYAR'ı seçin ve bu Bulut PC'ler için sağlamayı yeniden denemek için bu seçeneği belirtin.

Bulut BILGISAYARı hazırlama durumlarının tam listesini ve bunların ne anlama gelenini görmek için bkz. Belge [](/windows-365/enterprise/device-management-overview#column-details) kitaplığında Bulut PC'ler için Windows 365 genel bakış.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/all-cloud-pcs-tab.png" alt-text="Tüm Bulut Windows 365 sekmesinin ekran görüntüsü." lightbox="../media/m365-lighthouse-win365-page-overview/all-cloud-pcs-tab.png":::

## <a name="azure-network-connections-tab"></a>Azure ağ bağlantıları sekmesi

Azure ağ bağlantıları sekmesindeki renkli ek açıklama çubuğu, aşağıdaki durumlara sahip tüm müşteri kiracılar genelinde Azure ağ bağlantılarının toplam sayısını görüntüler: Başarılı bağlantılar ve Başarısız bağlantılar.

Ek açıklama çubuğunun altındaki listede, tüm Azure ağ bağlantılarını ve bunların bağlantı durumunu görüntüleyebilirsiniz.

Belirli bir sağlama durumuyla bağlantıları görmek için, listeye filtre yapmak için ek açıklama çubuğundan bu durumu seçin. Belirli bir veya birden çok müşteri kiracısına yönelik bağlantı durumlarını görmek için, Listeyi **filtrelemek için** Kiracılar açılan menüsünü kullanın.

Listede bir işlem veya sorun gidermeniz gerekirse, aşağıdaki Bağlantı ayrıntılarını görüntüle'yi **Microsoft Endpoint Manager**.

Azure ağ bağlantıları sekmesi de aşağıdaki seçenekleri içerir:

- **Yenile:** En güncel bağlantı verilerini almak için seçin.
- **Dışarı aktar:** Bağlantı verilerini virgülle ayrılmış değerler (Excel) dosyasına dışarı .csv seçin.
- **Arama:** Belirli bir bağlantıyı hızla bulmak için anahtar sözcükleri girin.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/azure-network-connections-tab.png" alt-text="Azure ağ bağlantıları sekmesinin ekran görüntüsü." lightbox="../media/m365-lighthouse-win365-page-overview/azure-network-connections-tab.png":::

## <a name="related-content"></a>İlgili içerik

[Bu ne Windows 365?](/windows-365/overview) (article)\
[Windows 365 bilgisayarlar için cihaz yönetimine genel bakış](/windows-365/enterprise/device-management-overview) (makale)\
[Microsoft 365 Lighthouse SSS](m365-lighthouse-faq.yml) (makale)