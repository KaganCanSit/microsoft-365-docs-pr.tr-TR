---
title: Microsoft 365 Lighthouse'da Cihaz uyumluluğu sayfasına genel bakış
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
description: Microsoft 365 Lighthouse kullanan Yönetilen Hizmet Sağlayıcıları (MSP) için Cihaz uyumluluğu sayfası hakkında bilgi edinin.
ms.openlocfilehash: e5440d89a34593655076cb91a348a176590dc52f
ms.sourcegitcommit: 339d2c2ffea06726f69429f73c1113c649f37b18
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2022
ms.locfileid: "65023711"
---
# <a name="overview-of-the-device-compliance-page-in-microsoft-365-lighthouse"></a>Microsoft 365 Lighthouse'da Cihaz uyumluluğu sayfasına genel bakış

Microsoft 365 Lighthouse, sol gezinti bölmesinde **Cihazlar'ı** seçerek Cihaz uyumluluğu sayfasını açarak tüm müşteri kiracılarınız için Intune cihaz uyumluluğuyla ilgili içgörüleri ve bilgileri görüntülemenizi sağlar. Bu sayfadan kiracılar genelinde uyumluluk durumuna genel bir bakış elde edebilir, her kiracı için cihazların listesini görüntüleyebilir ve uyumluluk ilkeleri ve ayarlarıyla ilgili durum raporları alabilirsiniz.

## <a name="overview-tab"></a>Genel Bakış sekmesi  
  
Genel Bakış sekmesinde kiracılarınız genelinde cihaz uyumluluk durumunu görüntüleyebilir, aylık cihaz uyumluluk eğilimlerine göz atabilir ve cihazların kendilerine uyumluluk ilkeleri atanıp atanmadığını izleyebilirsiniz. Ayrıca, koşullu erişim ilkeleri kullanılarak zorunlu kılınan cihaz uyumluluk gereksinimi olmayan kiracı sayısını da görebilirsiniz. Daha fazla ayrıntı görmek için **Daha fazla görüntüle'yi** seçebilirsiniz.

Belirli bir müşteri kiracısının ayrıntılı cihaz uyumluluk bilgilerini almak için, söz konusu kiracının durum sütunlarından herhangi birinin altında bir değer seçin. Bu, seçili kiracının cihaz uyumluluk ayrıntılarını görüntüleyebilmeniz için Cihazlar sekmesini açar.

Cihaz uyumluluk verilerini virgülle ayrılmış Excel değerler (.csv) dosyasına aktarmak için **Dışarı Aktar'ı** seçin.

:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/device-overview-tab.png" alt-text="Genel Bakış sekmesinin ekran görüntüsü." lightbox="../media/m365-lighthouse-device-compliance-page-overview/device-overview-tab.png":::

## <a name="devices-tab"></a>Cihazlar sekmesi

Cihazlar sekmesinde, renkli count-annotation çubuğu tüm müşteri kiracılarınızda şu uyumluluk durumlarına sahip toplam cihaz sayısını görüntüler: Uyumlu, Uyumlu değil, Yetkisiz kullanım süresinde ve Değerlendirilmedi. Farklı uyumluluk durumları hakkında daha fazla bilgi için bkz. [İzleme Intune Cihaz uyumluluk ilkeleri](/mem/intune/protect/compliance-policy-monitor).

Hangi kiracıların belirli bir uyumluluk durumuna sahip cihazları olduğunu görmek için, listeyi filtrelemek için count-annotation çubuğundan bu durumu seçin. Belirli bir veya daha fazla müşteri kiracısının cihaz uyumluluk durumlarını görmek için **Kiracılar** açılan menüsünü kullanarak listeyi filtreleyin.

Bu cihazın geçerli uyumluluk durumu hakkında daha fazla ayrıntı görüntülemek için listeden herhangi bir cihaz adını seçin. Sorunu gidermeniz veya daha fazla işlem yapmanız gerekiyorsa cihazı eşitleyebilir veya yeniden başlatabilir ya **da cihazı Microsoft Endpoint Manager'da görüntüle'yi** seçebilirsiniz.

> [!NOTE]
> Bir cihazı yeniden başlattığınızda, cihaz sahibi otomatik olarak bilgilendirilmez ve kaydedilmemiş çalışmayı kaybedebilir. Bu nedenle, bir cihazı yeniden başlatmadan önce cihaz sahibini bilgilendirmek isteyebilirsiniz.

Cihazlar sekmesi aşağıdaki seçenekleri de içerir:

- **Ihracat:** Cihaz uyumluluk verilerini virgülle ayrılmış Excel değerler (.csv) dosyasına aktarmak için seçin.
- **Yenileme:** En güncel cihaz uyumluluk verilerini almak için öğesini seçin.
- **Eşitleme:** Listeden Uyumlu değil, Yetkisiz kullanım süresinde veya Değerlendirilmedi durumuna sahip bir veya daha fazla cihaz seçin ve ardından bu cihazları Intune ile giriş yapmaya zorlamak ve onlara atanmış olan tüm ilkeleri hemen almaya zorlamak için bu seçeneği belirleyin.
- **Yeni -den başlatın:** Listeden Uyumlu değil, Yetkisiz kullanım süresi içinde veya Değerlendirilmedi durumuna sahip bir veya daha fazla cihaz seçin ve ardından bu cihazları yeniden başlatmak için bu seçeneği belirleyin.
- **Arama:** Listede belirli bir cihazı hızla bulmak için anahtar sözcükler girin.
 
:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/devices-device-tab.png" alt-text="Cihazlar sekmesinin ekran görüntüsü." lightbox="../media/m365-lighthouse-device-compliance-page-overview/devices-device-tab.png":::

## <a name="policies-tab"></a>İlkeler sekmesi

İlkeler sekmesinde, **kiracılarınız** genelinde cihaz uyumluluk ilkelerini görüntüleyebilir ve Karşılaştır seçeneğini kullanarak aynı platform türünde iki veya üç ilkeyi karşılaştırabilirsiniz.

Belirli bir platformdaki cihazların ilkelerini görmek için, listeyi filtrelemek için **işletim sistemi** açılan menüsünü kullanın. Belirli bir veya daha fazla müşteri kiracısının ilkelerini görmek için **Kiracılar** açılan menüsünü kullanarak listeyi filtreleyin.

Bu ilke hakkında daha fazla ayrıntı görüntülemek için listeden herhangi bir ilke adını seçin. Eylem gerçekleştirmeniz veya ek bilgiler görmeniz gerekiyorsa **Bu ilkeyi Microsoft Endpoint Manager'de görüntüle'yi** seçin.

İlkeler sekmesi aşağıdaki seçenekleri de içerir:

- **Ihracat:** Cihaz uyumluluk ilkesi verilerini virgülle ayrılmış Excel değerler (.csv) dosyasına dışarı aktarmak için seçin.
- **Yenileme:** En güncel cihaz uyumluluk ilkesi verilerini almak için öğesini seçin.
- **Arama:** Listede belirli bir cihaz uyumluluk ilkesini hızla bulmak için anahtar sözcükler girin.

:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/devices-policies-tab.png" alt-text="İlkeler sekmesinin ekran görüntüsü." lightbox="../media/m365-lighthouse-device-compliance-page-overview/devices-policies-tab.png":::

## <a name="settings-tab"></a>Ayarlar sekmesi

Ayarlar sekmesi, kiracı cihazlarında uyumlu olmayan ayarların toplu bir raporunu sağlar. 

Belirli bir platformdaki cihazların uyumlu olmayan ayarlarını görmek için **Platform** açılan menüsünü kullanarak listeyi filtreleyin. Belirli bir veya daha fazla müşteri kiracısının uyumlu olmayan ayarlarını görmek için **Kiracılar** açılan menüsünü kullanarak listeyi filtreleyin.

Belirli bir uyumlu olmayan ayara sahip cihazları olan kiracıların listesini görüntüleyebileceğiniz bir bölme açmak için listeden uyumlu olmayan herhangi bir ayar adı seçin. Burada, belirli bir uyumlu olmayan ayara sahip olan kiracı içindeki cihazlar hakkındaki bilgileri görüntülemek için listeden herhangi bir kiracıyı seçerek detaya gidebilirsiniz. Ayrıca, sorun gidermeniz veya daha fazla işlem yapmanız gerekiyorsa cihazı eşitleyebilir veya yeniden başlatabilir ya **da cihazı Microsoft Endpoint Manager'de görüntüle'yi** seçebilirsiniz.

Ayarlar sekmesi aşağıdaki seçenekleri de içerir:

- **Ihracat:** Uyumlu olmayan ayarlar verilerini virgülle ayrılmış Excel değerler (.csv) dosyasına dışarı aktarmak için seçin.
- **Yenileme:** En güncel uyumlu olmayan ayarlar verilerini almak için öğesini seçin.
- **Arama:** Listede belirli bir uyumlu olmayan ayarı hızla bulmak için anahtar sözcükler girin.

:::image type="content" source="../media/m365-lighthouse-device-compliance-page-overview/device-settings-tab.png" alt-text="Ayarlar sekmesinin ekran görüntüsü." lightbox="../media/m365-lighthouse-device-compliance-page-overview/device-settings-tab.png":::

## <a name="related-content"></a>İlgili içerik

[Microsoft 365 Lighthouse Windows 365 (Bulut Bilgisayarları) sayfasına genel bakış](m365-lighthouse-win365-page-overview.md) (makale)\
[Microsoft 365 Lighthouse SSS](m365-lighthouse-faq.yml) (makale)
