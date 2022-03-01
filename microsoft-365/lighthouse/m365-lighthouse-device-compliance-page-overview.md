---
title: Microsoft 365 Lighthouse Uyumluluğu sayfasına genel bakış
f1.keywords: NOCSH
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
description: Yönetilen Servis Sağlayıcıları (MSP) Microsoft 365 Lighthouse, Cihaz uyumluluğu sayfası hakkında bilgi edinebilirsiniz.
ms.openlocfilehash: d1c4cb8fde2d3f653e77020e4ad29f70da266a06
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996589"
---
# <a name="microsoft-365-lighthouse-device-compliance-page-overview"></a>Microsoft 365 Lighthouse Uyumluluğu sayfasına genel bakış

> [!NOTE]
> Bu makalede açıklanan özellikler Önizleme'dedir, değişebilir ve yalnızca gereksinimleri karşılayacak iş ortakları tarafından [kullanılabilir](m365-lighthouse-requirements.md). Henüz oturum açmadıysanız Microsoft 365 Lighthouse için [kaydolma'ya Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

Microsoft 365 Lighthouse, Sol gezinti bölmesindeKimlik uyumluluğu sayfasını açmak için Cihazlar'ı seçerek Intune cihaz uyumluluğu ile ilgili içgörüleri ve bilgileri tüm müşteri kiracılarınız için görüntülemenize olanak tanır. Bu sayfadan kiracılar genelinde uyumluluk durumuna genel bir bakış elde edebilirsiniz, her kiracının cihazlarının listesini ekleyebilirsiniz ve uyumluluk ilkeleriyle ayarları hakkında durum raporlarına bakabilirsiniz.

## <a name="overview-tab"></a>Genel Bakış sekmesi  
  
Genel Bakış sekmesinde kiracılar genelinde cihaz uyumluluğu durumunu görebilir, aylık cihaz uyumluluk eğilimlerini görebilir ve cihazlara uyumluluk ilkeleri atanmış olup olmadığını izleyebilirsiniz. Ayrıca, koşullu erişim ilkeleri kullanılarak zorunlu kılınan cihaz uyumluluğu gereksiniminin kaç kiracıda olmadığını da görebilirsiniz. Daha fazla ayrıntı **görmek için Daha fazla** görüntüle'yi seçin.

Belirli bir müşteri kiracısına ilişkin ayrıntılı cihaz uyumluluğu bilgilerini almak için söz konusu kiracının durum sütunlarının altında bir değer seçin. Böylece, seçilen kiracının cihaz uyumluluk ayrıntılarını görüntüleyebilirsiniz.

Cihaz uyumluluk verilerini virgülle ayrılmış değerler (Excel) dosyasına dışarı .csv Dışarı Aktar'ı **seçin**.

:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/device-overview-tab.png" alt-text="Genel Bakış sekmesinin ekran görüntüsü." lightbox="../media/m365-lighthouse-device-compliance-page-overview/device-overview-tab.png":::

## <a name="devices-tab"></a>Cihazlar sekmesi

Cihazlar sekmesindeki renkli sayma ek açıklaması çubuğu, tüm müşteri kiracıları genelinde aşağıdaki uyumluluk durumlarına sahip cihazların toplam sayısını görüntüler: Uyumlu, Uyumlu değil, Yetkisiz kullanım süresi ve Değerlendirilemedi. Farklı uyumluluk durumları hakkında daha fazla bilgi için bkz [. Intune Cihaz uyumluluk ilkelerini izleme](/mem/intune/protect/compliance-policy-monitor).

Belirli bir uyumluluk durumuna sahip kiracıların cihazlarını görmek için, bu durumu sayma çubuğundan seçerek listeye filtre ekleyin. Belirli bir veya birden çok müşteri kiracısına yönelik cihaz uyumluluğu durumlarını görmek için, Listeyi **filtrelemek için** Kiracılar açılan menüsünü kullanın.

O cihazın geçerli uyumluluk durumu hakkında daha fazla ayrıntı görüntülemek için listeden herhangi bir cihaz adını seçin. Sorunu gidermeniz veya başka bir işlem başlatmanız gerekirse, cihazı eşit **Microsoft Endpoint Manager** yeniden başlatabilirsiniz veya Cihazı şu cihazda görüntüle'yi seçin.

> [!NOTE]
> Cihazı yeniden başlattıktan sonra, cihaz sahibine otomatik olarak bu durum bildirlanmaz ve çalışmanızı kaybedebilir. Bu nedenle, cihazı yeniden başlatmadan önce cihaz sahibine bunu bildirebilirsiniz.

Cihazlar sekmesi aşağıdaki seçenekleri de içerir:

- **Dışarı aktar:** Cihaz uyumluluk verilerini virgülle ayrılmış değerler (Excel) dosyasına dışarı .csv seçin.
- **Yenile:** En güncel cihaz uyumluluk verilerini almak için seçin.
- **Eşitle:** Listeden Uyumlu değil, Yetkisiz kullanım süresi veya Değerlendirilemedi durumuna sahip bir veya daha fazla cihaz seçin ve ardından bu cihazları Intune ile iadeye zorlar ve atanmış olan tüm ilkeleri hemen alırlar.
- **Yeniden başlat:** Listeden Uyumlu değil, Yetkisiz kullanım süresi veya Değerlendirilemedi durumuna sahip bir veya daha fazla cihaz seçin ve bu cihazları yeniden başlatmak için bu seçeneği belirtin.
- **Arama:** Listede belirli bir cihazı hızla bulmak için anahtar sözcükleri girin.
 
:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/devices-device-tab.png" alt-text="Cihazlar sekmesinin ekran görüntüsü." lightbox="../media/m365-lighthouse-device-compliance-page-overview/devices-device-tab.png":::

## <a name="policies-tab"></a>İlkeler sekmesi

İlkeler sekmesinde Karşılaştır seçeneğini kullanarak kiracılar genelinde cihaz uyumluluk ilkelerini görüntüleyebilirsiniz ve aynı platform türünde iki veya üç **ilkeyi karşılaştırabilirsiniz** .

Belirli bir platformda yer alan cihazlara yönelik ilkeleri görmek için **, listeyi filtrelemek** için işletim sistemi açılan menüsünü kullanın. Belirli bir veya birden çok müşteri kiracısına yönelik ilkeleri görmek için **, Listeyi** filtrelemek için Kiracılar açılan menüsünü kullanın.

İlke hakkında daha fazla ayrıntı görüntülemek için, listede herhangi bir ilke adını seçin. Bir işlem yapmak veya ek bilgiler görmek için Bu ilkeyi şu dosyada **görüntüle'yi Microsoft Endpoint Manager**.

İlkeler sekmesi aşağıdaki seçenekleri de içerir:

- **Dışarı aktar:** Cihaz uyumluluk ilkesi verilerini bir virgülle ayrılmış değerler (Excel) dosyasına dışarı .csv seçin.
- **Yenile:** En güncel cihaz uyumluluk ilkesi verilerini almak için seçin.
- **Arama:** Listede belirli bir cihaz uyumluluk ilkesi hemen bulmak için anahtar sözcükleri girin.

:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/devices-policies-tab.png" alt-text="İlkeler sekmesinin ekran görüntüsü." lightbox="../media/m365-lighthouse-device-compliance-page-overview/devices-policies-tab.png":::

## <a name="settings-tab"></a>Ayarlar sekmesi

Aşağıdaki Ayarlar, kiracı cihazları genelinde uyumlu olmayan ayarların toplu bir raporunu sağlar. 

Belirli bir platformda yer alan cihazlara yönelik uyumlu olmayan ayarları görmek için, **Listeyi** filtrelemek için Platform açılan menüsünü kullanın. Bir veya birden çok müşteri kiracısına yönelik uyumlu olmayan ayarları görmek için, Listeyi filtrelemek **için** Kiracılar açılan menüsünü kullanın.

Belirli uyumlu olmayan ayarı olan cihazlara sahip kiracıların listesini görüntüleyebilirsiniz bir bölme açmak için, listede uyumlu olmayan ayarlardan herhangi birini seçin. Buradan, listede herhangi bir kiracıyı seçerek söz gel ve söz gel bu kiracının içinde belirli uyumlu olmayan ayara sahip cihazlarla ilgili bilgileri görüntüye kadar detaya inebilirsiniz. Ayrıca cihazı eşitler veya yeniden başlatabilirsiniz ya da sorun **gidermeniz ya da başka bir işlem Microsoft Endpoint Manager** Cihazda görüntüle'yi seçin.

Tablo Ayarlar aşağıdaki seçenekleri de içerir:

- **Dışarı aktar:** Uyumlu olmayan ayarlar verilerini bir virgülle ayrılmış değerler (Excel) dosyasına dışarı .csv seçin.
- **Yenile:** En güncel uyumlu olmayan ayarlar verilerini almak için bunu seçin.
- **Arama:** Listede belirli bir uyumlu olmayan ayarı hızla bulmak için anahtar sözcükleri girin.

:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/device-settings-tab.png" alt-text="Ekran görüntüsü Ayarlar görüntüsü." lightbox="../media/m365-lighthouse-device-compliance-page-overview/device-settings-tab.png":::

## <a name="related-content"></a>İlgili içerik

[Windows 365 (Bulut BILGISAYARLAR) sayfasına genel bakış](m365-lighthouse-win365-page-overview.md) (makale)\
[Microsoft 365 Lighthouse SSS](m365-lighthouse-faq.yml) (makale)
