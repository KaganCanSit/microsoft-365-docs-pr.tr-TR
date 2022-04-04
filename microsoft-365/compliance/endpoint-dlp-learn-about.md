---
title: Uç nokta Microsoft 365 kaybı önleme hakkında bilgi
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
description: 'Microsoft 365 noktası veri kaybını önleme önleme, bu dosyalar için dosya etkinliklerinin ve koruyucu eylemlerin izlenmesini uç noktalara genişlettir. Dosyalar Uyumluluk çözümsinde görünür hale gelir '
ms.openlocfilehash: 031d1d80dd6700939c9d73cc82350b7abc30c132
ms.sourcegitcommit: 0ae89b71b202aceabd5061f0d5b46d030d93e931
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2022
ms.locfileid: "64520793"
---
# <a name="learn-about-microsoft-365-endpoint-data-loss-prevention"></a>Uç nokta Microsoft 365 kaybı önleme hakkında bilgi

Hassas olmaya karar Microsoft 365 üzerinde gerçekleştirilen eylemleri izlemek ve bu öğelerin madde dışı olarak paylaşımını önlemeye yardımcı olmak için, veri kaybı önleme (DLP) önlemeyi kullanabilirsiniz. DLP hakkında daha fazla bilgi için bkz. [Veri kaybını önleme hakkında bilgi.](dlp-learn-about-dlp.md)

Uç nokta veri kaybı **önleme (Uç** Nokta DLP), DLP'nin etkinlik izleme ve koruma özelliklerini Windows 10, Windows 11 ve macOS (Catalina 10.15 ve daha yüksek) cihazlarda fiziksel olarak depolanan hassas öğelere genişletmektedir. Cihazlar uyumluluk çözümlerine Microsoft 365, kullanıcıların hassas öğelerle yaptıklarına ilişkin bilgiler etkinlik gezgininde görünür hale gelir ve DLP ilkeleri aracılığıyla bu öğeler [](data-classification-activity-explorer.md) üzerinde koruyucu işlemler [gerçekleştirebilirsiniz](create-test-tune-dlp-policy.md).

> [!TIP]
> Çıkarılabilir depolama alanı için cihaz denetimi arıyorsanız, bkz. Çıkarılabilir [Uç Nokta için Microsoft Defender Çıkarılabilir Depolama'Depolama Access Control](../security/defender-endpoint/device-control-removable-storage-access-control.md#microsoft-defender-for-endpoint-device-control-removable-storage-access-control).

> [!NOTE]
> Uyumluluk Microsoft 365 içinde, hassas öğelerin DLP ilkesi değerlendirmesi merkezi olarak gerçekleşir, dolayısıyla ilkeler ve ilke güncelleştirmelerinin tek tek cihazlara dağıtılması için zaman gecikmesi olmaz. Uyumluluk merkezinde bir ilke güncelleştirildiğinde, bu güncelleştirmelerin hizmet genelinde eşitlenmesi genellikle yaklaşık bir saat sürer. İlke güncelleştirmeleri eşitlensin mi, hedeflenen cihazlardaki öğeler bir sonraki erişilse veya değiştirildiğinde otomatik olarak yeniden değerlendirilir.

## <a name="endpoint-activities-you-can-monitor-and-take-action-on"></a>İzlemek ve üzerinde işlem gerçekleştirebilirsiniz uç nokta etkinlikleri

Microsoft Endpoint DLP, kullanıcıların fiziksel olarak fiziksel olarak depolanan Windows 10, Windows 11 veya macOS cihazlarını kullanan aşağıdaki etkinlik türlerini denetlemenizi ve yönetmenizi sağlar.

|Etkinlik |Açıklama  |Windows 10 1809 ve sonrası/ Windows 11| macOS Catalina 10.15 (önizleme) | Denetlenebilir/Kısıtlanabilir|
|---------|---------|---------|---------|---------|
|bulut hizmetine yükleme veya izin verilmeyen tarayıcılarla erişme    | Kullanıcı bir öğeyi kısıtlanmış bir hizmet etki alanına karşıya yükleme girişiminde bulunsa veya bir öğeye tarayıcı üzerinden erişmeye çalışır.  DLP'de izin verilmeyen bir tarayıcı olarak listelenen bir tarayıcı kullanıyorsa, karşıya yükleme etkinliği engellenir ve kullanıcı Microsoft Edge. Microsoft Edge sonra, DLP ilkesi yapılandırmasına göre karşıya yükleme veya erişime izin verme veya erişimi engelleme         |destek | destek|denetlenebilir ve kısıtlanabilir|
|başka bir uygulamaya kopyalama    |Kullanıcı, korumalı bir öğeden bilgi kopyalamaya ve sonra bunu başka bir uygulamaya, işlemeye veya öğeye yapıştırmaya çalışır. Aynı uygulama, süreç veya öğe içindeki bilgileri kopyalama ve kopyalama, bu etkinlik tarafından algılanmaz.|destek|destek         | denetlenebilir ve kısıtlanabilir|
|USB çıkarılabilir medyaya kopyalama |Kullanıcı, bir öğeyi veya bilgileri çıkarılabilir medyaya veya USB cihazına kopyalamayı ne zaman denemesi olduğunu algılar.|destek|destek         | denetlenebilir ve kısıtlanabilir|
|ağ paylaşımına kopyalama    |Kullanıcının bir öğeyi ağ paylaşımına veya eşlenmiş ağ sürücüsüne kopyalamayı denemesi ile ilgili algılama |destek|destek         |denetlenebilir ve kısıtlanabilir|
|belge yazdırma    |Kullanıcının korumalı bir öğeyi yerel bir yazıcıya veya ağ yazıcıya yazdırmayı denemesi üzerine bunu algılar.|destek|destek|denetlenebilir ve kısıtlanabilir         |
|uzak oturuma kopyalama|Kullanıcının bir öğeyi uzak masaüstü oturumuna kopyalamayı denemesi ile ilgili algılama |destek|desteklenmiyor|  denetlenebilir ve kısıtlanabilir|
|Bluetooth cihazına kopyalama|Kullanıcının izin verilmeyen bir Bluetooth uygulamasına öğe kopyalamayı denemesi (Uç nokta DLP ayarlarında izin verilmeyen kullanıcı aps'ler listesinde Bluetooth olduğunu algılar).|destek|desteklenmiyor| denetlenebilir ve kısıtlanabilir|
|öğe oluşturma|Kullanıcı bir öğe oluşturduğunda algılar|destek | |denetlenebilir|
|öğeyi yeniden adlandırma|Kullanıcının bir öğeyi ne zaman yeniden adlandır olduğunu algılar|destek | |denetlenebilir|

## <a name="monitored-files"></a>Izlenen dosyalar

Uç nokta DLP, bu dosya türlerinin izlenmesini destekler. DLP, bir ilke eşleşmesi olsa bile, bu dosya türlerinin etkinliklerini denetimler. 

- Word dosyaları
- PowerPoint dosya yükleme
- Excel dosya yükleme
- PDF dosyaları
- .csv dosya yükleme
- .tsv dosyaları
- .txt dosya yükleme
- .rtf dosyaları
- .c dosyaları
- .class dosyaları
- .cpp dosyaları
- .cs dosyaları
- .h dosyaları
- .java dosyaları
 
Yalnızca ilke eşleşmelerinden verileri izlemek için, uç nokta DLP genel ayarlarında Cihazlar için  her zaman denetim dosyası etkinliğini kapatabilirsiniz.

> [!NOTE]
> Cihazlar için  her zaman dosya etkinliğini denetle ayarı açıksa, cihaz herhangi bir ilke tarafından hedefli bile olsa tüm Word, PowerPoint, Excel, PDF ve .csv dosyalarına yönelik etkinlikler her zaman denetlenır.

> [!TIP]
> Desteklenen tüm dosya türlerinde etkinliklerin denetlen olduğundan emin olmak için, özel bir [DLP ilkesi oluşturun](create-test-tune-dlp-policy.md).

Uç nokta DLP, MIME türüne göre etkinlik tabanlı olarak izler, dolayısıyla dosya uzantısı değişse bile etkinlikler yakalanır.

### <a name="file-types-preview"></a>Dosya türleri (önizleme)

Dosya Türleri, belirli iş akışlarını veya iş alanlarını korumak için kullanılan bir dosya biçimleri grubudır. DLP ilkelerinize koşullar olarak bir veya birden çok Dosya türü kullanabilirsiniz.

|Dosya Türü |Uygulama  |izlenen dosya uzantıları  |
|---------|---------|---------|
|sözcük işleme |Word, PDF | .doc, .docx, .docm, .dot, .dotx, .dotm, .docb, .pdf |
|elektronik tablo    |Excel, CSV, TSV |.xls, .xlsx, .xlt, .xlm, .xlsm, .xltx, .xltm, .xlsb, .xlw, .csv, .tsv         |
|sunu |PowerPoint|.ppt, .pptx, .pos, .pps, .pptm, .potx, .potm, .ppam, .ppsx|
|Arşiv  |dosya arşivi ve sıkıştırma araçları | .zip, .zipx, .rar, .7z, .tar, .gz        |
|E-posta    |Outlook |.pst, .ost, .msg         |

### <a name="file-extensions-preview"></a>Dosya uzantıları (önizleme)

Dosya türleri, bir ilkede koşul olarak listeleniz gereken dosya uzantılarını kapsıyorsa, bunun yerine, dosya uzantılarını virgülle ayrılmış olarak kullanabilirsiniz.

> [!IMPORTANT]
> Dosya uzantıları ve dosya türleri seçenekleri, aynı kuralda koşullar olarak kullanılamaz. Bunları aynı ilkede koşullar olarak kullanmak istemiyorsanız, bunların ayrı kurallarda olması gerekir. 

> [!IMPORTANT]
> Bu Windows sürümleri Dosya türlerini ve Dosya uzantısı özelliklerini destekler:
>- Windows 10 20H1/20H2/21H1 (KB 5006738)
>- Windows 10 19H1/19H2 (KB 5007189)
>- Windows 10 RS5 (KB 5006744)


## <a name="whats-different-in-endpoint-dlp"></a>Uç Nokta DLP'sinde farklar

Uç Nokta DLP'sine başlamadan önce dikkat etmek gereken birkaç ek kavram vardır.

### <a name="enabling-device-management"></a>Cihaz yönetimini etkinleştirme

Cihaz yönetimi, cihazlardan telemetri toplamaya olanak sağlayan ve Uç Nokta DLP ve [Insider Risk](insider-risk-management.md) yönetimi gibi uyumluluk çözümlerini Microsoft 365 uyumluluk çözümlerine getiren işlevdir. DLP ilkeleri içinde konum olarak kullanmak istediğiniz tüm cihazları eklemelisiniz.

> [!div class="mx-imgBorder"]
> ![cihaz yönetimini etkinleştirin.](../media/endpoint-dlp-learn-about-1-enable-device-management.png)

Ekleme ve çıkarma, Cihaz yönetim merkezinden indiren betikler yoluyla ele alındır. Merkezde, şu dağıtım yöntemlerinin her biri için özel betikler vardır:

- yerel betik (en çok 10 makine)
- Grup ilkesi
- System Center Configuration Manager (sürüm 1610 veya sonrası)
- Mobil Cihaz Yönetimi/Microsoft Intune
- Kalıcı olmayan makinelerde VDI ekleme betikleri

> [!div class="mx-imgBorder"]
> ![cihaz ekleme sayfasına gidin.](../media/endpoint-dlp-learn-about-3-device-onboarding-page.png)

 Cihazları almak için Uç [Nokta DLP Microsoft 365 ile çalışmaya](endpoint-dlp-getting-started.md) başlama yordamlarını kullanın.

Uç Nokta için Microsoft Defender aracılığıyla [cihazlarınız](/windows/security/threat-protection/) varsa, bu cihazlar otomatik olarak cihaz listesinde görünür. Uç nokta **DLP'lerini kullanmak** için cihaz izlemeyi açabilirsiniz.

> [!div class="mx-imgBorder"]
> ![yönetilen cihazlar listesi.](../media/endpoint-dlp-learn-about-2-device-list.png)

### <a name="viewing-endpoint-dlp-data"></a>Uç Nokta DLP verilerini görüntüleme

Uç nokta cihazlarında zorunlu kılınan DLP ilkeleriyle ilgili uyarıları, [DLP Uyarıları Yönetim Panosu'ne gidip görüntüleyebilirsiniz](dlp-configure-view-alerts-policies.md).

> [!div class="mx-imgBorder"]
> ![Uyarı bilgileri.](../media/Alert-info-1.png)

Ayrıca, aynı panoda zengin meta verilerle ilişkilendirilmiş olayın ayrıntılarını da görüntüleyebilirsiniz

> [!div class="mx-imgBorder"]
> ![olay bilgilerine bakın.](../media/Event-info-1.png)

Bir cihaz alındıktan sonra, konum olarak cihazları olan DLP ilkelerini yapılandırmadan ve dağıtmadan önce bile, denetlenen etkinliklerle ilgili bilgiler Etkinlik gezginine akar.

> [!div class="mx-imgBorder"]
> ![etkinlik gezgininde uç nokta dlp olayları.](../media/endpoint-dlp-learn-about-4-activity-explorer.png)

Uç nokta DLP, denetlenen etkinlik hakkında kapsamlı bilgi toplar.

Örneğin, bir dosya çıkarılabilir USB medyaya kopyalandı ise, etkinlik ayrıntılarında şu öznitelikleri görüyorsunuz:

- etkinlik türü
- istemci IP'sini
- hedef dosya yolu
- timestamp oldu
- dosya adı
- kullanıcı
- dosya uzantısı
- dosya boyutu
- hassas bilgi türü (varsa)
- sha1 değeri
- sha256 değeri
- önceki dosya adı
- konum
- üst
- dosya yolu
- kaynak konum türü
- platform
- cihaz adı
- hedef konum türü
- kopyayı gerçekleştiren uygulama
- Uç Nokta için Microsoft Defender kimliğini girin (varsa)
- çıkarılabilir medya cihazı üreticisi
- çıkarılabilir medya cihaz modeli
- çıkarılabilir medya cihazı seri numarası

> [!div class="mx-imgBorder"]
> ![usb etkinliği özniteliklerine kopyala' bağlantısına kopyalayın.](../media/endpoint-dlp-learn-about-5-activity-attributes.png)

## <a name="next-steps"></a>Sonraki adımlar

Artık Uç Nokta DLP hakkında bilgi edin öğrendiğinize göre, sonraki adımlarınız:

1. [Cihazları Windows 10 veya Windows 11 cihazlara eklemeye Microsoft 365 genel bakış](device-onboarding-overview.md)
1. [macOS cihazlarının Microsoft 365'e katılımına genel bakış (önizleme)](device-onboarding-macos-overview.md)
1. [Uç noktada veri kaybı önleme ayarlarını yapılandırma](dlp-configure-endpoint-settings.md)
1. [Microsoft Uç Noktası veri kaybını önlemeyi kullanma](endpoint-dlp-using.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Endpoint veri kaybı önleme ile çalışmaya başlama](endpoint-dlp-getting-started.md)
- [Microsoft Uç Noktası veri kaybını önlemeyi kullanma](endpoint-dlp-using.md)
- [Veri kaybı önleme hakkında daha fazla bilgi edinme](dlp-learn-about-dlp.md)
- [Bir DLP ilkesi oluşturma, test etme ve ayarlama](create-test-tune-dlp-policy.md)
- [Kullanmaya başlayın gezgini ile çalışma](data-classification-activity-explorer.md)
- [Uç Nokta için Microsoft Defender](/windows/security/threat-protection/)
- [Insider Risk yönetimi](insider-risk-management.md)
