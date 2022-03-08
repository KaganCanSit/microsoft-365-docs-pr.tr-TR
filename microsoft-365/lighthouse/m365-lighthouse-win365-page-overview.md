---
title: Microsoft 365 Lighthouse Windows 365 (Bulut BILGISAYARLAR) sayfasına genel bakış
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
description: Microsoft 365 Lighthouse kullanarak Yönetilen Hizmet Sağlayıcıları (MSP)'ler için, Windows 365 (Bulut PC) sayfası hakkında bilgi edinebilirsiniz.
ms.openlocfilehash: 60b96974e0070e4a151484a162c3eafc18d0bf4a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63315533"
---
# <a name="windows-365-cloud-pcs-page-overview"></a>Windows 365 (Bulut BILGISAYARLAR) sayfasına genel bakış  
  
Windows 365, Microsoft Endpoint Manager (MEM) yöneticilerinin Windows lisansına sahip olan kullanıcıları için Bulut PC'leri hazırlamalarına ve yönetmelerine olanak sağlayan bulut tabanlı bir hizmettir. Windows 365, cihaz yönetimi için MEM ile ve tüm müşteri kiracılarında Bulut bilgisayarların iş Microsoft 365 Lighthouse için Microsoft 365 Lighthouse ile tamamen tümleşiktir.

365'Windows daha fazla bilgi için bkz[. Windows 365 nedir?](/windows-365/overview) 365 gereksinimlerinin Windows için bkz. [Windows 365 gereksinimleri](/windows-365/enterprise/requirements).

> [!IMPORTANT]
> Her müşteri kiracısı [için Bulut PC sağlamak için MEM'ye](https://go.microsoft.com/fwlink/p/?linkid=2150463) gidip bu bilgisayarları Deniz Feneri'nde yönetemenizi gerekir. Deniz Feneri'nin dışından sağ şey sağ şey değil.

Müşteri kiracınız için Bulut PC'ler sağlanan Windows 365 kartı, Microsoft 365 Giriş sayfasındaki Bulut PC'lerde sağlamada başarısız olan Bulut BILGISAYAR sayısı ve şirket içi ağ bağlantısı hatalarının sayısı gibi gerekli durumlarda kısa bir uyarı sağlar. Ayrıntılı durumu almak için Windows 365 kartının düğmesini seçerek (veya sol gezinti bölmesinde **Windows 365'i** seçin) Windows 365 sayfasını açın. Bu sayfadan, müşteri kiracınıza atanan Bulut PC'lere genel bir bakış elde eder, yönetmek istediğiniz tüm Bulut bilgisayarların ve atandığı kiracıların listesini ekleyebilirsiniz ve müşteri kiracıları ile Azure Active Directory (Azure AD) ile bunların durumları arasındaki şirket içi ağ bağlantılarını görüntüleyebilirsiniz.

## <a name="overview-tab"></a>Genel Bakış sekmesi

Genel Bakış sekmesindeki renkli ek açıklama çubuğu, aşağıdaki durumlara sahip tüm müşteri kiracıları genelinde Bulut PC'lerin veya şirket içi ağ bağlantılarının toplam sayısını gösterir: Başarısız ağ bağlantıları, Sağlanamadı, Sağlama başarısız oldu ve Yakında Yeniden Sağlama başarısız oldu.

Ek açıklama çubuğunun altındaki listede her müşteri kiracısı için Bulut Bilgisayar durumlarının dökümünü görebilirsiniz. Hangi kiracılarda belirli bir durumda Bulut PC olduğunu görmek için, bu durumu sayma çubuğundan seçerek listeye filtre ekleyin. Belirli bir veya birden çok müşteri kiracısı için Bulut Bilgisayarı'nın durumunu görmek için, **Listeyi filtrelemek** için Kiracılar açılan menüsünü kullanın.

Belirli bir müşteri kiracısına ilişkin ayrıntılı durum bilgilerini almak için, o kiracının durum sütunlarının herhangi biri altında bir değer seçin. Değerin hangi sütunda olduğuna bağlı olarak, **Şirket** içi ağ bağlantıları veya Tüm **bulut** PC'ler sekmesi açılır ve daha fazla bilgi gösterir.

Genel Bakış sekmesi aşağıdaki seçenekleri de içerir:

- **Yenile:** En güncel Bulut Bilgisayar verilerini almak için seçin.
- **Dışarı aktar:** Bulut Bilgisayar verilerini virgülle ayrılmış değerler (Excel) dosyasına dışarı .csv seçin.
- **Arama:** Listede belirli bir Bulut Bilgisayarı'nın yerini hızla bulmak için anahtar sözcükleri girin.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/win365-overview-tab.png" alt-text="Windows 365'e Genel Bakış sekmesinin ekran görüntüsü.":::

## <a name="all-cloud-pcs-tab"></a>Tüm Bulut Bilgisayarlar sekmesi

Tüm Bulut PC'ler sekmesinde renkli ek açıklama çubuğu, aşağıdaki durumlara sahip tüm müşteri kiracılar genelinde Bulut PC'lerin toplam sayısını görüntüler: Sağlandı, Sağlanamadı, Sağlama başarısız oldu ve Yakında Geri Alma.

Tüm Bulut PC'leri ve bunların hazırlama durumunu ek açıklama çubuğunun altındaki listede görüntüleyebilirsiniz. Aşağıdaki bilgiler sağlanır:

- **Bulut bilgisayar adı:** Bulut bilgisayara atanan ad.
- **Kiracı:** Bir Bulut bilgisayarının sağladığı müşteri kiracısı.
- **Cihaz adı:** Intune cihaz adı: Bulut PC için benzersiz bir tanımlayıcı.
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

Bulut PC hazırlama durumlarının tam listesini ve bunların ne anlama geliyorlarını görmek için bkz. Windows [](/windows-365/enterprise/device-management-overview#column-details) 365 belge kitaplığında Bulut PC'ler için cihaz yönetimine genel bakış.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/all-cloud-pcs-tab.png" alt-text="Windows 365 Tüm Bulut Bilgisayarları sekmesinin ekran görüntüsü.":::

## <a name="on-premises-network-connections-tab"></a>Şirket içi ağ bağlantıları sekmesi

Şirket içi ağ bağlantıları sekmesindeki renkli ek açıklama çubuğu, aşağıdaki durumlara sahip tüm müşteri kiracıları genelindeki şirket içi ağ bağlantılarının toplam sayısını görüntüler: Başarılı bağlantılar ve Başarısız bağlantılar.

Count-annotation çubuğunun altındaki listede, tüm şirket içi ağ bağlantılarını ve bunların bağlantı durumunu görüntüleyebilirsiniz.

Belirli bir sağlama durumuyla bağlantıları görmek için, listeye filtre yapmak için ek açıklama çubuğundan bu durumu seçin. Belirli bir veya birden çok müşteri kiracısına yönelik bağlantı durumlarını görmek için, Listeyi **filtrelemek için** Kiracılar açılan menüsünü kullanın.

Listede bir işlem veya sorun gidermeniz gerekirse, aşağıdaki Bağlantı ayrıntılarını görüntüle'yi **Microsoft Endpoint Manager**.

Şirket içi ağ bağlantıları sekmesi de aşağıdaki seçenekleri içerir:

- **Yenile:** En güncel bağlantı verilerini almak için seçin.
- **Dışarı aktar:** Bağlantı verilerini virgülle ayrılmış değerler (Excel) dosyasına dışarı .csv seçin.
- **Arama:** Belirli bir bağlantıyı hızla bulmak için anahtar sözcükleri girin.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/on-prem-network-connections-tab.png" alt-text="Windows 365 Şirket içi ağ bağlantıları sekmesinin ekran görüntüsü.":::

## <a name="related-content"></a>İlgili içerik

[365 Windows nedir?](/windows-365/overview) (article)\
[Windows bilgisayarlar için 365 cihaz yönetimine genel bakış](/windows-365/enterprise/device-management-overview) (makale)\
[Microsoft 365 Lighthouse SSS](m365-lighthouse-faq.yml) (makale)