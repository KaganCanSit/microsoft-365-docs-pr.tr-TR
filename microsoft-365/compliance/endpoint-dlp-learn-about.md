---
title: uç nokta veri kaybı önleme Microsoft 365 hakkında bilgi edinin
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
description: 'uç nokta veri kaybını önleme Microsoft 365 dosya etkinliklerinin ve bu dosyalar için koruyucu eylemlerin izlenmesini uç noktalara genişletir. Dosyalar Uyumluluk çözümlerinde görünür hale getiriliyor '
ms.openlocfilehash: f32e84434258ff4b4c5ea6af24f69c607952b56a
ms.sourcegitcommit: 1c5f9d17a8b095cd88b23f4874539adc3ae021de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2022
ms.locfileid: "64714559"
---
# <a name="learn-about-microsoft-365-endpoint-data-loss-prevention"></a>uç nokta veri kaybı önleme Microsoft 365 hakkında bilgi edinin

Hassas olduğunu belirlediğiniz öğelerde gerçekleştirilen eylemleri izlemek ve bu öğelerin yanlışlıkla paylaşılmasını önlemeye yardımcı olmak için Microsoft 365 veri kaybı önlemeyi (DLP) kullanabilirsiniz. DLP hakkında daha fazla bilgi için bkz. [Veri kaybını önleme hakkında bilgi edinin](dlp-learn-about-dlp.md).

**Uç nokta veri kaybı önleme** (Endpoint DLP), DLP'nin etkinlik izleme ve koruma özelliklerini fiziksel olarak Windows 10, Windows 11 ve macOS (Catalina 10.15 ve üzeri) cihazlarda depolanan hassas öğelere genişletir. Cihazlar Microsoft 365 uyumluluk çözümlerine eklendikten sonra, kullanıcıların hassas öğelerle yaptıklarıyla ilgili bilgiler [etkinlik gezgininde](data-classification-activity-explorer.md) görünür hale getirilir ve [DLP ilkeleri](create-test-tune-dlp-policy.md) aracılığıyla bu öğeler üzerinde koruyucu eylemler uygulayabilirsiniz.

> [!TIP]
> Çıkarılabilir depolama birimi için cihaz denetimi arıyorsanız bkz. [Uç Nokta için Microsoft Defender Cihaz Denetimi Çıkarılabilir Depolama Access Control](../security/defender-endpoint/device-control-removable-storage-access-control.md#microsoft-defender-for-endpoint-device-control-removable-storage-access-control).

> [!NOTE]
> Microsoft 365 Uyumluluğunda, hassas öğelerin DLP ilkesi değerlendirmesi merkezi olarak gerçekleşir, bu nedenle ilkelerin ve ilke güncelleştirmelerinin tek tek cihazlara dağıtılması için zaman gecikmesi yoktur. Uyumluluk merkezinde bir ilke güncelleştirildiğinde, bu güncelleştirmelerin hizmet genelinde eşitlenmesi genellikle yaklaşık bir saat sürer. İlke güncelleştirmeleri eşitlendikten sonra, hedeflenen cihazlardaki öğeler bir sonraki erişildiğinde veya değiştirildiğinde otomatik olarak yeniden değerlendirilir.

## <a name="endpoint-activities-you-can-monitor-and-take-action-on"></a>İzleyebileceğiniz ve üzerinde eylem gerçekleştirebileceğiniz uç nokta etkinlikleri

Microsoft Endpoint DLP, kullanıcıların fiziksel olarak Windows 10, Windows 11 veya macOS cihazlarında depolanan hassas öğeler üzerinde gerçekleştirecekleri aşağıdaki etkinlik türlerini denetlemenize ve yönetmenize olanak tanır.

|Etkinlik |Açıklama  |Windows 10 1809 ve üzeri/ Windows 11| macOS Catalina 10.15 (önizleme) | Denetlenebilir/kısıtlanabilir|
|---------|---------|---------|---------|---------|
|bulut hizmetine yükleme veya izin verilmeyen tarayıcılarla erişim    | Bir kullanıcının kısıtlanmış bir hizmet etki alanına öğe yüklemeyi veya bir öğeye tarayıcı üzerinden erişmeyi denediğinde algılar.  DLP'de izin verilmeyen bir tarayıcı olarak listelenen bir tarayıcı kullanıyorlarsa, karşıya yükleme etkinliği engellenir ve kullanıcı Microsoft Edge kullanmak üzere yeniden yönlendirilir. Microsoft Edge, DLP ilke yapılandırmasına göre karşıya yükleme veya erişime izin verir veya erişimi engeller         |Desteklenen | Desteklenen|denetlenebilir ve kısıtlanabilir|
|başka bir uygulamaya kopyalama    |Kullanıcı korumalı bir öğeden bilgi kopyalamaya çalıştığında bunu algılar ve ardından başka bir uygulama, işlem veya öğeye yapıştırır. Aynı uygulama, işlem veya öğe içindeki bilgilerin kopyalanması ve yapıştırılması bu etkinlik tarafından algılanmaz.|Desteklenen|Desteklenen         | denetlenebilir ve kısıtlanabilir|
|USB çıkarılabilir medyaya kopyalama |Kullanıcının bir öğeyi veya bilgileri çıkarılabilir medyaya veya USB cihazına kopyalamaya çalıştığında algılar.|Desteklenen|Desteklenen         | denetlenebilir ve kısıtlanabilir|
|ağ paylaşımına kopyalama    |Kullanıcının bir öğeyi bir ağ paylaşımına veya eşlenmiş ağ sürücüsüne kopyalamaya çalıştığında algılar |Desteklenen|Desteklenen         |denetlenebilir ve kısıtlanabilir|
|belge yazdırma    |Kullanıcının korumalı bir öğeyi yerel veya ağ yazıcısına yazdırmaya çalıştığında algılar.|Desteklenen|Desteklenen|denetlenebilir ve kısıtlanabilir         |
|uzak oturuma kopyalama|Kullanıcının bir öğeyi uzak masaüstü oturumuna kopyalamaya çalıştığında algılar |Desteklenen|desteklenmiyor|  denetlenebilir ve kısıtlanabilir|
|Bluetooth cihazına kopyalama|Kullanıcının bir öğeyi izin verilmeyen bir Bluetooth uygulamasına (Uç Nokta DLP ayarlarında izin verilmeyen Bluetooth ap'ler listesinde tanımlandığı gibi) kopyalamaya çalıştığında algılar.|Desteklenen|desteklenmiyor| denetlenebilir ve kısıtlanabilir|
|öğe oluşturma|Kullanıcı öğe oluşturduğunda algılar|Desteklenen | |Denetlene -bilir|
|öğeyi yeniden adlandırma|Kullanıcının bir öğeyi yeniden adlandırdığında algılar|Desteklenen | |Denetlene -bilir|

## <a name="best-practice-for-endpoint-dlp-policies"></a>Uç nokta DLP ilkeleri için en iyi yöntem

Kredi kartı numaraları içeren tüm öğelerin Finans departmanı kullanıcılarının uç noktalarını bırakmasını engellemek istediğinizi varsayalım. Aşağıdakiler önerilir:

- Bir ilke oluşturun ve bu ilkeyi uç noktalara ve bu kullanıcı grubuna göre kapsamına alın.
- İlkede korumak istediğiniz bilgi türünü algılayan bir kural oluşturun. Bu durumda **, içerik** *Hassas bilgi türü** olarak ayarlanır ve **Kredi Kartı'nın** seçilmesini sağlar.
- Her etkinliğin eylemlerini **Engelle** olarak ayarlayın.

DLP ilkelerinizi tasarlama konusunda daha fazla rehberlik için bkz. [Veri kaybı önleme ilkesi](dlp-policy-design.md) tasarlama.

## <a name="monitored-files"></a>İzlenen dosyalar

Uç nokta DLP, bu dosya türlerinin izlenmesini destekler. DLP, ilke eşleşmesi olmasa bile bu dosya türlerinin etkinliklerini denetler. 

- Word dosyaları
- dosyaları PowerPoint
- dosyaları Excel
- PDF dosyaları
- dosyaları .csv
- .tsv dosyaları
- dosyaları .txt
- .rtf dosyaları
- .c dosyaları
- .class dosyaları
- .cpp dosyaları
- .cs dosyaları
- .h dosyaları
- .java dosyaları
 
Yalnızca ilke eşleşmelerindeki izleme verilerini istiyorsanız, uç nokta DLP genel ayarlarındaki **cihazlar için dosya etkinliğini her zaman denetle** seçeneğini kapatabilirsiniz.

> [!NOTE]
> **Cihazlar için dosya etkinliğini her zaman denetle** ayarı açıksa, herhangi bir Word, PowerPoint, Excel, PDF ve .csv dosyasındaki etkinlikler, cihaz herhangi bir ilke tarafından hedeflenmese bile her zaman denetlenir.

> [!TIP]
> Etkinliklerin desteklenen tüm dosya türleri için denetlendiğinden emin olmak için [özel bir DLP ilkesi](create-test-tune-dlp-policy.md) oluşturun.

Uç nokta DLP, MIME türüne göre etkinliği izler, bu nedenle dosya uzantısı değiştirilse bile etkinlikler yakalanır.

### <a name="file-types-preview"></a>Dosya türleri (önizleme)

Dosya Türleri, belirli iş akışlarını veya iş alanlarını korumak için kullanılan bir dosya biçimleri gruplandırmadır. DLP ilkelerinizde koşul olarak bir veya daha fazla Dosya türü kullanabilirsiniz.

|Dosya Türü |Uygulama  |izlenen dosya uzantıları  |
|---------|---------|---------|
|sözcük işleme |Word, PDF | .doc, .docx, .docm, .dot, .dotx, .dotm, .docb, .pdf |
|Elektronik tablo    |Excel, CSV, TSV |.xls, .xlsx, .xlt, .xlm, .xlsm, .xltx, .xltm, .xlsb, .xlw, .csv, .tsv         |
|Sunum |PowerPoint|.ppt, .pptx, .pos, .pps, .pptm, .potx, .potm, .ppam, .ppsx|
|Arşiv  |dosya arşiv ve sıkıştırma araçları | .zip, .zipx, .rar, .7z, .tar, .gz        |
|E-posta    |Outlook |.pst, .ost, .msg         |

### <a name="file-extensions-preview"></a>Dosya uzantıları (önizleme)

Dosya türleri bir ilkede koşul olarak listelemeniz gereken dosya uzantılarını kapsamazsa, bunun yerine virgülle ayrılmış dosya uzantılarını kullanabilirsiniz.

> [!IMPORTANT]
> Dosya uzantıları ve dosya türleri seçenekleri aynı kuralda koşul olarak kullanılamaz. Bunları aynı ilkede koşul olarak kullanmak istiyorsanız, bunların ayrı kurallarda olması gerekir. 

> [!IMPORTANT]
> Bu Windows sürümleri Dosya türlerini ve Dosya uzantısı özelliklerini destekler:
>- Windows 10 sürümleri 20H1/20H2/21H1 (KB 5006738)
>- Windows 10 sürümleri 19H1/19H2 (KB 5007189)
>- Windows 10 RS5 (KB 5006744)


## <a name="whats-different-in-endpoint-dlp"></a>Uç Nokta DLP'sindeki farklar

Uç Nokta DLP'sini incelemeden önce bilmeniz gereken birkaç ek kavram vardır.

### <a name="enabling-device-management"></a>Cihaz yönetimini etkinleştirme

Cihaz yönetimi, cihazlardan telemetri toplanmasını sağlayan ve Uç Nokta DLP ve [Insider Risk yönetimi](insider-risk-management.md) gibi Microsoft 365 uyumluluk çözümlerine getiren işlevselliktir. DLP ilkelerinde konum olarak kullanmak istediğiniz tüm cihazları eklemeniz gerekir.

> [!div class="mx-imgBorder"]
> ![cihaz yönetimini etkinleştirin.](../media/endpoint-dlp-learn-about-1-enable-device-management.png)

Ekleme ve çıkarma işlemleri, Cihaz yönetim merkezinden indirdiğiniz betikler aracılığıyla işlenir. Merkezde şu dağıtım yöntemlerinin her biri için özel betikler vardır:

- yerel betik (en fazla 10 makine)
- Grup ilkesi
- System Center Configuration Manager (sürüm 1610 veya üzeri)
- Mobil Cihaz Yönetimi/Microsoft Intune
- Kalıcı olmayan makineler için VDI ekleme betikleri

> [!div class="mx-imgBorder"]
> ![cihaz ekleme sayfası.](../media/endpoint-dlp-learn-about-3-device-onboarding-page.png)

 Cihazları eklemek için [Microsoft 365 Uç Nokta DLP'sini kullanmaya başlama'daki](endpoint-dlp-getting-started.md) yordamları kullanın.

[Cihazları Uç Nokta için Microsoft Defender](/windows/security/threat-protection/) aracılığıyla eklediyseniz, bu cihazlar otomatik olarak cihaz listesinde gösterilir. Uç nokta **DLP'sini kullanmak için cihaz izlemeyi açabilirsiniz** .

> [!div class="mx-imgBorder"]
> ![yönetilen cihazlar listesi.](../media/endpoint-dlp-learn-about-2-device-list.png)

### <a name="viewing-endpoint-dlp-data"></a>Uç Nokta DLP verilerini görüntüleme

DLP [Uyarıları Yönetim Panosu'na](dlp-configure-view-alerts-policies.md) giderek uç nokta cihazlarında zorunlu kılınan DLP ilkeleriyle ilgili uyarıları görüntüleyebilirsiniz.

> [!div class="mx-imgBorder"]
> ![Uyarı bilgileri.](../media/Alert-info-1.png)

Aynı panoda zengin meta verilerle ilişkili olayın ayrıntılarını da görüntüleyebilirsiniz

> [!div class="mx-imgBorder"]
> ![olay bilgileri.](../media/Event-info-1.png)

Bir cihaz eklendikten sonra, cihaz içeren DLP ilkelerini konum olarak yapılandırmadan ve dağıtmadan önce bile denetlenen etkinlikler hakkındaki bilgiler Etkinlik gezginine akar.

> [!div class="mx-imgBorder"]
> ![etkinlik gezgininde endpoint dlp olayları.](../media/endpoint-dlp-learn-about-4-activity-explorer.png)

Uç nokta DLP, denetlenen etkinlik hakkında kapsamlı bilgiler toplar.

Örneğin, bir dosya çıkarılabilir USB medyasına kopyalanırsa etkinlik ayrıntılarında şu öznitelikleri görürsünüz:

- etkinlik türü
- istemci IP'i
- hedef dosya yolu
- oldu zaman damgası
- dosya adı
- Kullanıcı
- dosya uzantısı
- dosya boyutu
- hassas bilgi türü (varsa)
- sha1 değeri
- sha256 değeri
- önceki dosya adı
- Konum
- Üst
- Filepath
- kaynak konum türü
- Platform
- cihaz adı
- hedef konum türü
- kopyalamayı gerçekleştiren uygulama
- Uç Nokta için Microsoft Defender cihaz kimliği (varsa)
- çıkarılabilir medya cihazı üreticisi
- çıkarılabilir medya cihazı modeli
- çıkarılabilir medya cihazı seri numarası

> [!div class="mx-imgBorder"]
> ![usb etkinlik özniteliklerine kopyalayın.](../media/endpoint-dlp-learn-about-5-activity-attributes.png)

## <a name="next-steps"></a>Sonraki adımlar

Uç Nokta DLP hakkında bilgi edindiğinize göre, sonraki adımlarınız şunlardır:

1. [Microsoft 365 genel bakışa Windows 10 veya Windows 11 cihazları ekleme](device-onboarding-overview.md)
1. [macOS cihazlarının Microsoft 365'e katılımına genel bakış (önizleme)](device-onboarding-macos-overview.md)
1. [Uç noktada veri kaybı önleme ayarlarını yapılandırma](dlp-configure-endpoint-settings.md)
1. [Microsoft Endpoint veri kaybı önlemeyi kullanma](endpoint-dlp-using.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Endpoint veri kaybı önlemeyi kullanmaya başlama](endpoint-dlp-getting-started.md)
- [Microsoft Endpoint veri kaybı önlemeyi kullanma](endpoint-dlp-using.md)
- [Veri kaybı önleme hakkında daha fazla bilgi edinme](dlp-learn-about-dlp.md)
- [Bir DLP ilkesi oluşturma, test etme ve ayarlama](create-test-tune-dlp-policy.md)
- [Etkinlik gezgini ile Kullanmaya başlayın](data-classification-activity-explorer.md)
- [Uç Nokta için Microsoft Defender](/windows/security/threat-protection/)
- [Insider Risk yönetimi](insider-risk-management.md)
