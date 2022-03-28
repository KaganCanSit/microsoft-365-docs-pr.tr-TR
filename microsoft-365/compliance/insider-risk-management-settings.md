---
title: Insider risk yönetimi ayarları
description: Insider risk yönetimi ayarları hakkında bilgi edinmek için Microsoft 365
keywords: Microsoft 365, insider risk yönetimi, risk yönetimi, uyumluluk
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection:
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: 4b14f2def771294bdfa05109d6060242736f26d5
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754723"
---
# <a name="get-started-with-insider-risk-management-settings"></a>Insider risk yönetimi ayarlarıyla çalışmaya başlama

Insider risk yönetimi ayarları, ilke oluştururken seçtiğiniz şablondan bağımsız olarak tüm Insider risk yönetimi ilkeleri için geçerlidir. Ayarlar, tüm **Insider risk yönetimi** sayfalarının en üstünde yer alan Insider risk ayarları denetimi kullanılarak yapılandırılır. Bu ayarlar, aşağıdaki alanlar için ilke bileşenlerini kontrol sağlar:

- Gizlilik
- Göstergeler
- İlke zaman çizelgeleri
- Akıllı algılamalar
- Uyarıları dışarı aktarma
- Öncelik kullanıcı grupları (önizleme)
- Öncelikli fiziksel varlıklar (önizleme)
- Power Automate akışları (önizleme)
- Microsoft Teams (önizleme)
- Analiz
- Yönetici bildirimleri

Insider risk yönetimi ilkelerine başlamadan ve oluşturmadan önce, bu ayarları anlamak ve kuruma en uygun uyumluluk düzeylerini seçmek önemlidir.

## <a name="privacy"></a>Gizlilik

İlke eşleşmesi olan kullanıcıların gizliliğini korumak önemlidir ve insider risk uyarıları için veri araştırmasında ve çözümleme incelemesinde nesnenin daha yaygın korunmasına yardımcı olabilir. Insider risk ilkesi eşleşmesi olan kullanıcılar için, aşağıdaki ayarlardan birini seçebilirsiniz:

- **Kullanıcı adlarının anonimleştirilmiş** sürümlerini gösterme: Yöneticilerin, veri kullanıcılarının ve gözden geçirenlerin ilke uyarılarını kimlerle ilişkilendirilenleri görmelerini önlemek için anonimleştirilmiştir. Örneğin, 'Grace Taylor' kullanıcısı insider risk yönetim deneyiminin tüm alanlarında rastgele takma adla ('AnonIS8-988' gibi) görünebilir. Bu ayarın seçimi, geçerli ve geçmiş ilke eşleşmeleri olan tüm kullanıcıları anonim olarak uygular ve tüm ilkelere uygulanır. Bu seçenek seçildikten sonra, Insider risk uyarılarında yer alan kullanıcı profili bilgileri ve olay ayrıntıları kullanılamaz. Ancak kullanıcı adları, var olan ilkelere yeni kullanıcılar eklerken veya yeni ilkelere kullanıcı atarken görüntülenir. Bu ayarı kapatmayı seçerseniz, geçerli veya eski ilke eşleşmeleri olan tüm kullanıcılar için kullanıcı adları görüntülenir.

    >[!IMPORTANT]
    >başka sistemlerde veya başka sistemlerde Insider Microsoft 365 risk uyarısı veya vakaları olan kullanıcıların bilgi tutarlılığını korumak için, dışarı aktarma uyarıları için kullanıcı adları anonimliği korunmaz. Dışarı aktarıldı uyarılarda, her uyarı için kullanıcı adları görüntülenir.

- **Kullanıcı adlarının anonimleştirilmiş sürümlerini** gösterme: Uyarıların ve davaların tüm geçerli ve geçmiş ilke eşleşmeleri için kullanıcı adları görüntülenir. Tüm Insider risk yönetimi uyarıları ve vakaları için kullanıcı profil bilgileri (ad, unvan, diğer ad ve kuruluş veya bölüm) kullanıcı için görüntülenir.

![Insider risk yönetimi gizlilik ayarları.](../media/insider-risk-settings-privacy.png)

## <a name="indicators"></a>Göstergeler

Insider risk ilkesi şablonları algılamak ve araştırmak istediğiniz risk etkinlikleri türünü tanımlar. Her ilke şablonunda, belirli tetikleyicilere ve risk etkinliklerine karşılık gelen belirli göstergeler temellenir. Varsayılan olarak tüm göstergeler devre dışı bırakılmıştır ve insider risk yönetimi ilkesi yapılandırmadan önce bir veya birden çok ilke göstergesi seçmeniz gerekir.

Kullanıcılar gerekli bir eşiği karşıleyen ilke göstergeleriyle ilgili etkinlikler gerçekleştiriyorsa, uyarılar ilkeler tarafından tetiklenir. Insider risk yönetimi iki tür gösterge kullanır:

- **Olayları tetikleme**: Kullanıcının bir Insider risk yönetimi ilkesinde etkin olup olmadığını belirleyen olaylar. Kullanıcı bir Insider risk yönetimi ilkesine eklendiğinde tetikleyici olayı yoksa, kullanıcı etkinliği ilke tarafından değerlendirilmez. Örneğin, Kullanıcı A, kullanıcı ilke şablonundan ayrılarak Veri hırsızlığından oluşturulan bir ilkeye eklenir ve ilke ve İk bağlayıcısı Microsoft 365 yapılandırıldı. Kullanıcı A'nın İk bağlayıcısı tarafından bildirilen bir sonlandırma tarihine kadar Kullanıcı A etkinlikleri, riskle ilgili bu Insider risk yönetimi ilkesi tarafından değerlendirilmez. Tetikleyen bir diğer örnek de, kullanıcıda Veri sızıntıları ilkeleri  kullanılırken yüksek önem düzeyi olan bir DLP *ilkesi uyarısı olmasıdır*.
- **İlke göstergeleri**: Kapsam içi bir kullanıcının risk puanı belirlemek için kullanılan Insider risk yönetimi ilkelerine dahil edilen göstergeler. Bu ilke göstergeleri yalnızca kullanıcı için bir tetikleyici olayı oluştuğunda etkinleştirilir. İlke göstergelerinin bazı örnekleri, kullanıcının kişisel bulut depolama hizmetlerine veya taşınabilir depolama cihazlarına veri kopyalanması, kullanıcı hesabı Azure Active Directory'tan kaldırılmış olması veya kullanıcının şirket içi dosyaları ve klasörleri yetkisiz dış taraflarla paylaştığı durumdur.

Bazı ilke göstergeleri, belirli ilke şablonları için olayları tetikleyen olayları özelleştirmek için de kullanılabilir. Genel veri sızıntıları veya Öncelikli kullanıcı şablonlarının  Veri sızıntıları için ilke  sihirbazında yapılandırıldığında, bu göstergeler ilkeleriniz ve kullanıcılar ilke kapsamında olduğunda daha fazla esneklik ve özelleştirme sağlar. Buna ek olarak, bir ilkede daha ince  taneli denetim için bu tetikleyici göstergeleri için tek tek etkinlik eşikleri tanımlayabilirsiniz.

İlke göstergeleri aşağıdaki alanlara göre bölüm içerir. Insider risk ilkesi oluştururken her gösterge düzeyi için gösterge olayı sınırlarını etkinleştirmek ve özelleştirmek için göstergeleri seçebilirsiniz:

- **Office göstergelerini içerir**: Bunlar, e-posta SharePoint, posta Microsoft Teams ilke göstergeleridir.
- **Cihaz göstergeleri**: Bunlar, ağ üzerinden veya cihazlarla dosya paylaşma gibi etkinliklere yönelik ilke göstergeleri içerir. Göstergeler, yürütülebilir (yürütülebilir dosya) ve dinamik bağlantı kitaplığı (.exe) dosya etkinliği .dll etkinlikleri içerir. Cihaz *göstergeleri'yi* seçin. Etkinlik, Windows 10 Derleme 1809 veya sonraki bir derlemeye ve macOS (Catalina 10.15 veya sonraki) cihazlara yönelik olarak işlenir. Hem Windows macOS cihazları için cihazları uyumluluk merkezine eklemeniz gerekir. Cihaz göstergeleri, aynı zamanda Microsoft Edge Ve Google Chrome'da görüntülenilen, kopyalanan, paylaşılan veya yazdırılmış olmayan dosyalar için algılanmasına ve bu sinyallere yönelik izin işaretlerine yönelik tarayıcı sinyali algılamayı içerir. Cihazları Insider riskiyle tümleştirme Windows yapılandırma hakkında daha fazla bilgi için, bu makalenin Cihaz göstergelerini etkinleştirme [](insider-risk-management-settings.md#OnboardDevices) ve cihaz Windows cihaz ekleme bölümüne bakın. macOS cihazlarını Insider riskiyle tümleştirme için yapılandırma hakkında daha fazla bilgi için, bu makaledeki Cihaz göstergelerini etkinleştirme ve macOS cihazlarını ekleme bölümüne bakın. Tarayıcı sinyali algılama hakkında daha fazla bilgi için bkz [. Insider risk yönetimi tarayıcı sinyali algılama hakkında bilgi ve yapılandırma](insider-risk-management-browser-support.md).
- **Güvenlik ilkesi ihlal göstergesi (önizleme)**: Bunlar, uygulamalanmamış veya kötü amaçlı yazılım yüklemesi ile ilgili ya da güvenlik denetimlerini atlayan Uç Nokta için Microsoft Defender'ın göstergelerini içerir. Insider risk yönetiminde uyarı almak için, etkin bir Uç Nokta lisansı için Defender'nız ve Insider risk tümleştirmesi etkinleştirilmiş olmalıdır. Insider risk yönetimi tümleştirmesi için Uç Nokta için Defender'ı yapılandırma hakkında daha fazla bilgi için bkz. Uç Nokta için [Microsoft Defender'da gelişmiş özellikleri yapılandırma](/windows/security/threat-protection/microsoft-defender-atp/advanced-features\#share-endpoint-alerts-with-microsoft-compliance-center).
- **Sağlık kaydı erişim göstergeleri (önizleme)**: Bunlar hasta tıbbi kaydı erişimi için ilke göstergeleri içerir. Örneğin, elektronik tıbbi kayıtlar (EMR) sistem günlüklerinde bulunan hasta tıbbi kayıtlarına erişmeye çalıştınız, Insider risk yönetimi sağlık ilkeleriyle paylaşabilirsiniz. Insider risk yönetiminde bu tür uyarıları almak için, sağlıkla ilgili bir veri bağlayıcısı ve yapılandırılmış bir İk veri bağlayıcısı gerekir.
- **Fiziksel erişim göstergeleri (önizleme)**: Bunlar, hassas varlıklara fiziksel erişim için ilke göstergeleri içerir. Örneğin, fiziksel bajman sistemi günlükleriniz içinde kısıtlanmış bir alana erişmeye çalıştınız ve Insider risk yönetimi ilkeleriyle paylaşabilirsiniz. Insider risk yönetiminde bu tür uyarıları almak için, Insider risk yönetiminde öncelikli fiziksel varlıkları etkinleştirmiş ve Yapılandırılmış Fiziksel [badging](import-physical-badging-data.md) veri bağlayıcısı olmalıdır. Fiziksel erişimi yapılandırma hakkında daha fazla bilgi edinmek için, bu makalenin [Öncelikli fiziksel erişim](#priority-physical-assets-preview) bölümüne bakın.
- **Bulut Uygulamaları için Microsoft Defender göstergeleri (önizleme)**: Bunlar, Bulut Uygulamaları için Defender'ın paylaşılan uyarılarından gelen ilke göstergelerini içerir. Bulut Uygulamaları için Defender'da otomatik olarak etkinleştirilen anormal algılama, kullanıcılarınız ve ağınıza bağlı makine ve cihazlarınız genelinde çok sayıda davranışa yönelik sonuçları hemen algılamaya ve harmanlamaya başlar. Bu etkinlikleri Insider risk yönetimi ilkesi uyarılarına eklemek için bu bölümde bir veya birden çok gösterge seçin. Bulut Uygulamaları analizi ve anormal algılama için Defender hakkında daha fazla bilgi edinmek için bkz. [Davranış analizi ve anormal algılamayı öğrenme](/cloud-app-security/anomaly-detection-policy).
- **Risk puanı ilke ihlalleri**: Bunlar, bir gün boyunca kullanıcının normal etkinliğinin üzerinde olan veya daha önceki davaları ilke ihlali olarak çözümlenen kullanıcılar için risk puanının yükselt edilmesidir. Risk puanı etkinleştirnerek risk puanları ve bu tür etkinlikler için uyarı olasılığı artar. Kullanıcının bir günlük normal etkinliğinin üzerinde olan etkinliklerde, algılanan etkinlik kullanıcının normal davranışından saptayana kadar puanlar artırıldı. Önceki davaları ilke ihlali olarak çözümlenen kullanıcılar için, bir kullanıcının daha önce onaylandı olarak kabul edilen ilke ihlalini çözmüş birden çok durumu varsa puanlar artırıldı. Risk puanı, ancak bir veya daha fazla gösterge seçiliyse seçilebilir.

Bazı durumlarda, kurum içindeki Insider risk ilkelerine uygulanan insider risk ilkesi göstergelerini sınırlandırmanızı tercih etmiş olursunuz. Tüm Insider risk ilkelerinden devre dışı bırakarak, belirli alanlar için ilke göstergelerini kapatamazsiniz. Olayları tetikleyen olaylar yalnızca Genel veri sızıntıları veya Öncelik kullanıcı  şablonları tarafından veri sızıntıları *ile oluşturulan ilkelerde* değiştirilebilir. Diğer tüm şablonlardan oluşturulan ilkelerde özelleştirilebilir tetikleyici göstergeleri veya olayları yok.

Tüm Insider risk ilkelarında etkinleştirilmiş insider risk ilkesi göstergelerini tanımlamak için **, Insider risk** >  **ayarlarıİndicators** seçeneğine gidin ve bir veya birden çok ilke göstergesi seçin. Gösterge ayarları sayfasında seçilen göstergeler, ilke sihirbazında insider risk ilkesi oluşturulur veya düzenlerken tek tek yapılandırılamaz.

> [!NOTE]
> El ile eklenen yeni kullanıcıların Kullanıcılar panosunda görünmesi birkaç **saat sürebilir**. Bu kullanıcıların önceki 90 günlük etkinliklerinin 24 saate kadar görüntülemesi daha sürebilir. El ile eklenen kullanıcıların etkinliklerini görüntülemek için, Kullanıcılar panosunda kullanıcı seçin  ve ayrıntılar **bölmesindeki** Kullanıcı etkinliği sekmesini açın.

### <a name="enable-device-indicators-and-onboard-windows-devices"></a>Cihaz göstergelerini etkinleştirme ve cihaz Windows ekleme
<a name="OnboardDevices"> </a>

Windows cihazlarında risk etkinliklerinin izlenmesini etkinleştirmek ve bu etkinliklere yönelik ilke göstergeleri eklemek için Windows cihazlarında aşağıdaki gereksinimleri karşılamalı ve aşağıdaki ekleme adımlarını tamamlamanız gerekir.

#### <a name="step-1-prepare-your-endpoints"></a>1. Adım: Uç noktaları hazırlama

Insider risk Windows 10 raporlamayı planladınız tüm cihazların bu gereksinimleri karşı olduğundan emin olun.

1. Windows 10 x64 derleme 1809 veya sonraki bir sürümün çalışıyor olması ve 20 Şubat 2020'den [itibaren Windows 10 güncelleştirmesini (17763.1075 Işletim](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818) Sistemi Derlemesi) yüklemiş olması gerekir.
2. Windows 10 cihazında oturum açmak için kullanılan kullanıcı hesabının etkin bir Azure Active Directory (AAD) hesabı olması gerekir. En Windows 10, karma [AAD](/azure/active-directory/devices/concept-azure-ad-join), AAD veya Active Directory'ye katılmış ya da AAD olabilir.
3. Bulut Microsoft Edge etkinliğinin eylemlerini izlemek için uç nokta cihazına Microsoft Edge tarayıcısını yükleyin. Bkz[. Temel Microsoft Edge yeni Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium).

#### <a name="step-2-onboarding-devices"></a>2. Adım: Ekleme cihazları
<a name="OnboardStep2"> </a>

Cihazda Insider risk yönetimi etkinliklerini izlemek için önce cihaz izlemeyi etkinleştirmeniz ve uç noktalarınızı eklemeniz gerekir. Her iki eylem de Uyumluluk Microsoft 365 alınır.

Henüz eklememiş cihazları almak istediğiniz zaman, uygun betiği indirip aşağıdaki adımlarda ana hatları verilen şekilde dağıtın.

Uç nokta için [Microsoft Defender'a](/windows/security/threat-protection/) önceden cihazlarınız varsa, bunlar yönetilen cihazlar listesinde zaten görünür. [3. Adımı izleyin: Sonraki bölümde Uç nokta için Microsoft Defender'a cihaz](insider-risk-management-settings.md#OnboardStep3) girdiyebilirsiniz.

Bu dağıtım senaryosunda, henüz eklememiş cihazları ve diğer cihazlarda insider risk etkinliklerini izlemek Windows 10.

1. Dosyayı [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com).
2. Uyumluluk Merkezi ayarlar sayfasını açın ve Cihazları **ekleyin'i seçin**.

   > [!NOTE]
   > Cihaz eklemenin etkinleştirilmesi genellikle yaklaşık 60 saniye sürerken, Microsoft desteğiyle iletişime başlamadan önce lütfen 30 dakika kadar bekleyin.

3. Cihazlar **listesini açmak** için Cihaz **yönetimi'ne** tıklayın. Cihazları ekleyene kadar liste boş olacaktır.
4. Ekleme **işlemini başlamak** için Ekleme'yi seçin.
5. Dağıtım yöntemi listesinden daha fazla cihaza dağıtmak istediğiniz **yöntemi seçin** ve ardından paketi **indirin**.
6. Makine makineniz için [ekleme araçları ve yöntemlerinde uygun Windows 10 izleyin](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). Bu bağlantı sizi, 5. adımda seçtiğiniz dağıtım paketiyle eşleşmesi gereken Uç nokta için Microsoft Defender yordamlarına erişebilirsiniz.
    - Grup Windows 10 kullanarak makine ekleme
    - Windows kullanarak makine Microsoft Endpoint Configuration Manager
    - Mobil Windows 10 Yönetim araçlarını kullanarak makine ekleme
    - Yerel Windows 10 kullanarak makine ekleme
    - Kalıcı olmayan sanal masaüstü altyapısı (VDI) makinelerini ekleme.

Bitirilen ve uç nokta eklensin mi, cihaz listesinde görünür olmalıdır ve uç nokta denetim etkinliği günlüklerini Insider risk yönetimine bildirmeye başlar.

> [!NOTE]
> Bu deneyim lisans zorlaması altındadır. Gerekli lisans olmadan veriler görünür veya erişilebilir olmaz.

#### <a name="step-3-if-you-have-devices-onboarded-into-microsoft-defender-for-endpoint"></a>3. Adım: Uç Nokta için Microsoft Defender'a ekli cihazlarınız varsa
<a name="OnboardStep3"> </a>

Uç Nokta için Microsoft Defender zaten dağıtılmışsa ve raporlama uç noktaları varsa, bu uç noktaların hepsi yönetilen cihazlar listesinde görünür. 2. Adım: Cihazları ekleme bölümünü kullanarak kapsamı genişletmek için insider risk yönetimine yeni cihazlar [eklemeye devam](insider-risk-management-settings.md#OnboardStep2) edin.

1. Dosyayı [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com).
2. Uyumluluk Merkezi ayarlar sayfasını açın ve Cihaz izlemeyi **etkinleştir'i seçin**.
3. Cihazlar **listesini açmak** için Cihaz **yönetimi'ne** tıklayın. Zaten Uç Nokta için Microsoft Defender'a raporlama yapan cihazların listesini görüyor olun.
4. Daha **fazla cihaz eklemeye** ihtiyacınız varsa Ekleme'yi seçin.
5. Dağıtım yöntemi listesinden bu daha fazla cihaza dağıtmak istediğiniz **yöntemi seçin ve** sonra da Paketi **indir'i seçin**.
6. Makine makineniz için [ekleme araçları ve yöntemlerinde uygun Windows 10 izleyin](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). Bu bağlantı sizi, 5. adımda seçtiğiniz dağıtım paketiyle eşleşmesi gereken Uç nokta için Microsoft Defender yordamlarına erişebilirsiniz.
    - Grup Windows 10 kullanarak makine ekleme
    - Windows kullanarak makine Microsoft Endpoint Configuration Manager
    - Mobil Windows 10 Yönetim araçlarını kullanarak makine ekleme
    - Yerel Windows 10 kullanarak makine ekleme
    - Kalıcı olmayan sanal masaüstü altyapısı (VDI) makinelerini ekleme.

Bitirilen ve uç nokta ekleme yapıldıktan sonra, Cihazlar tablosu altında görünür  olmalıdır ve uç nokta denetim etkinliği günlüklerini Insider risk yönetimine bildirmeye başlar.

> [!NOTE]
>Bu deneyim lisans zorlaması altındadır. Gerekli lisans olmadan veriler görünür veya erişilebilir olmaz.

### <a name="enable-device-indicators-and-onboard-macos-devices"></a>Cihaz göstergelerini etkinleştirme ve macOS cihazları ekleme

macOS cihazları (Catalina 10.15 veya sonrası), Intune veya JAMF cihazlarında insider risk yönetimi ilkelerini desteklemek için Microsoft 365'ye Pro. Daha fazla bilgi ve yapılandırma kılavuzu için bkz. [macOS cihazlarını genel Microsoft 365 (önizleme) kullanma](device-onboarding-macos-overview.md).

### <a name="indicator-level-settings-preview"></a>Gösterge düzeyi ayarları (önizleme)

İlke sihirbazında bir ilke oluştururken, günlük risk etkinlikleri sayısının Insider risk uyarıları için risk puanını nasıl etkilesi gerektiğini yapılandırabilirsiniz. Bu gösterge ayarları, kuruluşta risk olaylarının yine olaylarının sayısının risk puanını ve bu olaylar için ilişkili uyarı önem derecesini nasıl etkileyeceğini denetlemenize yardımcı olur. Tercih ederseniz, etkinleştirilen tüm göstergeler için Microsoft tarafından önerilen varsayılan olay eşik düzeylerini de tutabilirsiniz.

Örneğin, insider risk ilkesi ayarlarında SharePoint göstergeleri etkinleştirmeye ve yeni Insider *risk Veri* sızıntıları ilkesi için göstergeleri yapılandırarak SharePoint etkinlikleri için özel eşikler ayarlamaya karar verirsiniz. Insider risk ilkesi sihirbazındayken, bu olaylarla ilişkilendirilmiş uyarılar için risk puanına etki etmek üzere her grup SharePoint göstergesi için üç farklı günlük etkinlik düzeyi yapılandırabilirsiniz.

![Insider risk yönetimi özel gösterge ayarları.](../media/insider-risk-custom-indicators.png)

İlk günlük etkinlik düzeyi için, etkinliklerin risk puanına daha düşük bir etki için günde *10* veya daha fazla etkinlik, olayların risk puanına orta düzeyde etki etmek için günde *20* veya daha fazla olay ve her gün *30* veya daha fazla olay, olayların risk puanına daha yüksek bir etkisi vardır. Bu ayarlar şu anlama geliyor:

- Etkinliği tetikledikten sonra SharePoint 1-9 arasında hata olayı varsa, risk puanları en az düzeyde etkilenir ve uyarı oluşturmama eğiliminde olur.
- Tetiklenen bir olaydan sonra SharePoint 10-19 arasında güvenlik düzeyi varsa, risk puanı yapısal olarak düşüktür ve uyarı önem düzeyi düşük düzeyde olur.
- Bir tetikleyiciden sonra SharePoint olan 20-29 arasında güvenlik düzeyi varsa, risk puanı yapısal olarak daha yüksektir ve uyarı önem düzeyi orta düzeyde olur.
- Bir tetikleyiciden sonra SharePoint 30 veya daha fazla olay varsa, risk puanı yapısal olarak daha yüksektir ve uyarı önem düzeyi yüksek düzeyde olur.

## <a name="policy-timeframes"></a>İlke zaman çerçeveleri

İlke zaman çerçeveleri, insider risk yönetimi ilke şablonlarının etkinliklerine ve etkinliklerine dayalı olarak ilke eşleşmelerinden sonra tetiklenen geçmiş ve gelecek gözden geçirme dönemlerini tanımlamanıza olanak sağlar. Seçtiğiniz ilke şablonuna bağlı olarak, aşağıdaki ilke zaman çerçeveleri kullanılabilir:

- **Etkinleştirme penceresi**: Tüm ilke şablonları için kullanılabilir; Etkinleştirme *penceresi* , pencerenin bir tetikleyici olayından sonra etkinleştiren **tanımlı** gün sayısıdır. İlkeye atanan tüm kullanıcılar için bir tetikleyici olayı oluştuğunda pencere 1 ile 30 gün arasında etkin hale gelir. Örneğin, insider risk yönetimi ilkesi yapılandırdı ve Etkinleştirme penceresini 30 *gün olarak* ayarlayın. İlkeyi yapılandırmanın üzerinden birkaç ay geçti ve ilkeye dahil olan kullanıcılardan biri için bir tetikleyici olayı gerçekleşir. Tetikleyen olay Etkinleştirme penceresini *etkinleştirir ve* tetiklenen olay gerçekleştikten sonra 30 gün boyunca bu kullanıcı için ilke etkin durumda olur.
- **Geçmiş etkinlik algılaması**: Tüm ilke şablonlarında kullanılabilir, Geçmiş  etkinlik algılaması, pencerenin tetikleyici olayından önce etkinleştiren tanımlı gün sayısıdır. İlkeye atanan tüm kullanıcılar için tetikleyici olayı oluşmadan önce pencere 0 ile 90 gün arasında etkin hale gelir. Örneğin, insider risk yönetimi ilkesi yapılandırdı ve Geçmiş etkinlik algılamayı 90 gün  olarak ayarlamış olursunuz. İlkeyi yapılandırmanın üzerinden birkaç ay geçti ve ilkeye dahil olan kullanıcılardan biri için bir tetikleyici olayı gerçekleşir. Tetikleyen olay Geçmiş etkinlik *algılamayı etkinleştirir ve* ilke tetikleyici olayından 90 gün önce bu kullanıcı için tarihi etkinlikleri toplar.

![Insider risk yönetimi zaman çerçevesi ayarları.](../media/insider-risk-settings-timeframes.png)

## <a name="intelligent-detections"></a>Akıllı algılamalar

Akıllı algılama ayarları, uyarılarda riskli etkinliklerin algılanmasında nasıl işlendiğine yardımcı olur. Bazı durumlarda, yoksaymak istediğiniz dosya türlerini tanımlamanız veya kullanıcılar için risk puanlarını artırmak üzere günlük etkinlikler için bir algılama düzeyini zorunlu kılınmak istiyor da olabilir. Dosya türü dışlamalarını kontrol etmek, sıra dışı etkinlikler için risk puanını artırmak ve dosya hacmi sınırlarını artırmak için bu ayarları kullanın.

### <a name="file-type-exclusions"></a>Dosya türü dışlamaları

Belirli dosya türlerini tüm Insider risk yönetimi ilkesi eşleştirmelerinin dışında tutmak için, dosya türü uzantılarını virgüllerle ayırarak girin. Örneğin, bazı müzik dosyası türlerini ilke eşleşmelerinin dışında tutmak için Dosya türü dışlamalar alanına *aac,mp3,wav,wma* **girebilirsiniz** . Bu uzantılara sahip dosyalar tüm Insider risk yönetimi ilkeleri tarafından yok sayılır.

### <a name="minimum-number-of-daily-events-to-boost-score-for-unusual-activity"></a>Alışılmış dışı etkinlikler için puanı artırmak için günlük en az etkinlik sayısı

Bu ayar ile, kullanıcı için alışılmış dışında kabul edilen etkinlik risk puanını artırmak için günlük kaç etkinliğin gerekli olduğunu tanımlayabilirsiniz. Örneğin, bu risk için 25 girersiniz. Kullanıcı son 30 gün içinde 10 dosyanın toplamını indirirse, ancak bir ilke 20 dosyayı bir günde indir olduğunu algılarsa, bu kullanıcının o gün indirdiği dosyaların sayısı bu risk için girdiğiniz dosya sayısından daha az olduğundan bu etkinliğin puanı artırmaz.

### <a name="alert-volume"></a>Uyarı sesi

Insider risk ilkeleri tarafından algılanan kullanıcı etkinliklerine belirli bir risk puanı atanır ve bu da uyarının önem derecesine (düşük, orta, yüksek) belirler. Varsayılan olarak, belirli miktarda düşük, orta ve yüksek önem düzeyi uyarıları oluşturacaktır; ancak sesi kendi ihtiyaçlarına göre artırabilir veya azaltebilirsiniz. Tüm Insider risk yönetimi ilkeleri için uyarı hacmini ayarlamak için, aşağıdaki ayarlardan birini seçin:

- **Daha az uyarı**: Tüm yüksek önem düzeyi uyarılarını, daha az orta önem düzeyi uyarılarını ve düşük önem düzeyine sahip uyarıları göresiniz. Bu ayar düzeyi bazı gerçek pozitif pozitif durumlarını kaçırabilirsiniz anlamına gelir.
- **Varsayılan ses** düzeyi: Tüm yüksek önem derecesi uyarılarını ve dengeli miktarda orta ve düşük önem düzeyi uyarısıyla karşı karşılarsiniz.
- **Daha fazla uyarı**: Tüm orta ve yüksek önem düzeyi uyarıları ve en düşük önem düzeyi uyarıları. Bu ayar düzeyi daha çok hatalı pozitif sonuç verir.

### <a name="microsoft-defender-for-endpoint-preview"></a>Uç Nokta için Microsoft Defender (önizleme)

[Uç Nokta için Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) , kurumsal ağların gelişmiş tehditleri engellemesini, algılamasını, araştırmasını ve yanıtlamasını önlemeye yardımcı olmak için tasarlanmış bir kurumsal uç nokta güvenlik platformudur. Organizasyonda güvenlik ihlallerinin daha iyi görünürlüğünü artırmak için, Insider risk yönetimi güvenlik ihlal ilkesi şablonlarından oluşturulan ilkelerde kullanılan etkinlikler için Uç nokta uyarıları için Defender'ı içeri aktararak ve filtresini gerçekleştirebilirsiniz.

İlgilenilen sinyal türlerine bağlı olarak, Uç nokta uyarısı için Defender üç durum bilgi durumuna bağlı olarak uyarıları Insider risk yönetimine aktarmayı seçebilirsiniz. İçeri aktarma işlemi için genel ayarlarda aşağıdaki uyarı üç durumlarından birini veya birden fazlasını tanımlayabilirsiniz:

- Unknown
- Yeni
- Devam ediyor
- Çözüldü

Uç Nokta için Defender'dan gelen uyarılar günlük olarak aktarılır. Seçtiğiniz öncelik durumuna bağlı olarak, Uç Nokta için Defender'da, üç durum bilgisinde değişiklikle aynı uyarı için birden çok kullanıcı etkinlikleri görebilir.

Örneğin, bu ayar için *Yeni, Sürüyor* ve Çözümlendi'yi seçerseniz, Uç Nokta için Microsoft Defender uyarısı oluşturulur ve durum Yeni *olduğunda, insider* riski olan kullanıcı için bir ilk uyarı etkinliği aktarılır. Uç Nokta için Defender değerlendirme durumu Sürüyor olarak değiştikçe *,* insider riski olan kullanıcı için bu uyarı için ikinci bir etkinlik içeri aktarılır. Çözümlendi'nin Uç Nokta triyaksı  için son Defender durumu ayar olduğunda, insider riski olan kullanıcı için bu uyarı için üçüncü bir etkinlik içeri aktarılır. Bu işlev, uç nokta uyarıları için Defender'ın ilerlemesini izlemesi ve araştırmalarının gerektirdiği görünürlük düzeyini seçmeye olanak sağlar.

> [!IMPORTANT]
> Güvenlik ihlal uyarılarını içeri aktaracak Defender Güvenlik Merkezi'nde Insider risk yönetimi tümleştirmesi için, kuruluşta Uç Nokta için Microsoft Defender For Endpoint'ı yapılandırmanız ve Insider risk yönetimi tümleştirmesi için Uç Nokta için Defender'ı etkinleştirmeniz gerekir. Insider risk yönetimi tümleştirmesi için Uç Nokta için Defender'ı yapılandırma hakkında daha fazla bilgi için bkz. Uç Nokta için [Defender'da gelişmiş özellikleri yapılandırma](/windows/security/threat-protection/microsoft-defender-atp/advanced-features\#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="domains"></a>Etki alanları

Etki alanı ayarları, belirli etki alanlarındaki etkinliklere yönelik risk düzeylerini tanımlamanıza yardımcı olur. Bu etkinlikler arasında dosya paylaşımı, e-posta iletileri gönderme, içerik indirme veya karşıya yükleme yer alır. Bu ayarlarda etki alanlarını belirterek, bu etki alanlarına yapılan etkinlikler için risk puanlama sayısını artırabilir veya azaltabilirsiniz.

Etki alanı ayarlarından her biri için bir etki alanı tanımlamak üzere Etki alanı ekle'yi kullanın. Buna ek olarak, kök etki alanlarının veya alt etki alanlarının çeşitlemelerini eşleşmeye yardımcı olması için joker karakter kullanabilirsiniz. Örneğin, sales.wingtiptoys.com ve support.wingtiptoys.com belirtmek için, bu alt etki alanlarıyla (ve aynı düzeydeki diğer alt etki alanlarıyla) eşleşmesi için '*.wingtiptoys.com' joker girdisini kullanırsınız. Kök etki alanı için çok düzeyli alt etki alanları belirtmek için, Çok Düzeyli Alt Etki Alanları Dahil Edin **onay kutusunu** seçmeniz gerekir.

Aşağıdaki etki alanı ayarlarının her biri için en çok 500 etki alanı girebilirsiniz:

- **Izin verilmeyen etki alanları:** Izin verilmeyen etki alanları belirterek, bu etki alanlarıyla yapılan etkinlikler daha yüksek risk *notlarına* sahip olur. Bazı örnekler, bir biriyle içerik paylaşma (örneğin, bir kullanıcıya e-posta adresi olan bir kullanıcıya gmail.com e-posta gönderme) ve kullanıcıların izin verilmeyen bu etki alanlarından bir cihaza içerik indirmesi gibi etkinliklerdir.
- **İzin verilen etki alanları:** İzin verilen etki alanlarıyla ilgili bazı etkinlikler ilkeleriniz tarafından yok sayılır ve uyarı oluşturmaz. Bu etkinlikler şunlardır:

    - Dış etki alanlarına gönderilen e-posta
    - Dış etki alanlarıyla paylaşılan dosyalar, klasörler, siteler
    - Dış etki alanlarına yüklenen dosyalar (Microsoft Edge kullanarak)

    Ayarlarda izin verilen etki alanları belirterek, bu etki alanlarıyla ilgili bu etkinlik, iç kuruluş etkinliğinin nasıl işlem gördüğüne benzer şekilde işlem gören bir işlemdir. Örneğin, burada etkinliklere yönelik eklenen etki alanları, içeriğin kuruluş dışındaki biriyle paylaşımını içerebilir (örneğin, e-posta adresini içeren birine gmail.com olabilir).

- **Üçüncü taraf etki alanları:** Organizasyonunız iş amaçlı (bulut depolama alanı gibi) üçüncü taraf etki alanları kullanıyorsa, cihaz göstergesiyle ilgili etkinliklere yönelik uyarılar aly için buraya bu etki alanlarını dahil edin. Üçüncü taraf bir *siteden* içerik indirmek için tarayıcı kullanın.

## <a name="export-alerts"></a>Uyarıları dışarı aktarma

Insider risk yönetimi uyarı bilgileri, Office 365 Management Activity API şeması kullanılarak güvenlik bilgileri ve etkinlik yönetimi (SIEM) ve güvenlik otomasyonu otomatik yanıtı (SOAR) [çözümlerine dışarı aktarılabilir](/office/office-365-management-api/office-365-management-activity-api-schema#security-and-compliance-alerts-schema). Uyarı bilgilerini, Office 365 bilgilerini yönetmek veya toplamak için kullanabileceği diğer uygulamalara dışarı aktarabilirsiniz. Uyarı bilgileri dışarı aktarıldı ve her 60 dakikada bir Yönetim Office 365 API'leri aracılığıyla kullanılabilir.

Ayrıca, kuruluşta Microsoft Sentinel kullanıyorsa, Insider risk uyarı bilgilerini Sentinel'e içeri aktararak ilk kullanımdan insider risk yönetimi veri bağlayıcısı da kullanabilirsiniz. Daha fazla bilgi için, Microsoft [Microsoft 365 Insider Risk Yönetimi (IRM) (Önizleme)](/azure/sentinel/data-connectors-reference#microsoft-365-insider-risk-management-irm-preview) makalesine bakın.

>[!IMPORTANT]
>başka sistemlerde veya başka sistemlerde Insider Microsoft 365 risk uyarısı veya vakaları olan kullanıcıların bilgi tutarlılığını korumak için, dışarı aktarma uyarıları için kullanıcı adları anonimliği korunmaz. Dışarı aktarıldı uyarılarda, her uyarı için kullanıcı adları görüntülenir.

API'leri kullanarak insider risk uyarı bilgilerini gözden geçirmek için:

1. Insider risk Office 365'da Kullanıcı Yönetimi Etkinlik **API'si desteğini etkinleştirin** >  **Ayarlar** >  **Export uyarıları**. Varsayılan olarak, bu ayar Microsoft 365 devre Microsoft 365 devre dışıdır.
2. Sık kullanılan denetim Office 365 *SecurityComplianceAlerts tarafından filtre uygulama*.
3. *SecurityComplianceAlerts'i* *InsiderRiskManagement kategorisine göre filtrele*.

![Insider risk yönetimi dışa aktarma uyarısı ayarları.](../media/insider-risk-settings-export.png)

Uyarı bilgileri, güvenlik ve uyumluluk uyarı şemasından ve genel Yönetim Office 365 şemasından bilgileri içerir.

Güvenlik ve Uyumluluk uyarı şeması için Insider risk yönetimi uyarıları için aşağıdaki alanlar & dışarı aktarıldı:

| **Alert parametresi** | **Açıklama** |
|:------------------|:----------------|
| AlertType | Uyarının türü *Özel'tir*.  |
| AlertId | Uyarının GUID'si. Insider risk yönetimi uyarıları çok önemli. Uyarı durumu değiştikleriyle aynı AlertID'ye sahip yeni bir günlük oluşturulur. Bu AlertID, bir uyarının güncelleştirmelerini birbiriyle bağlantılı yapmak için kullanılabilir. |
| Kategori | Uyarının kategorisi *InsiderRiskManagement olur*. Bu kategori, bu uyarıları diğer Güvenlik ve Uyumluluk uyarılarından & için kullanılabilir. |
| Açıklamalar | Uyarı için varsayılan açıklamalar. Değerler *Yeni Uyarı* (uyarı oluşturulduğunda günlüğe kaydedilir) ve Uyarı *Güncelleştirildi* (uyarıda güncelleştirme olduğunda günlüğe kaydedilir). Uyarının güncelleştirmelerini birbiriyle bağlantılı yapmak için AlertID'i kullanın. |
| Veri | Uyarıyla ilgili veriler, benzersiz kullanıcı kimliğini, kullanıcı asıl adını ve ilkeye kullanıcının tetiklendiğinde tarih ve saati (UTC) içerir. |
| Name | Uyarıyı oluşturan Insider risk yönetimi ilkesi için ilke adı. |
| PolicyId | Uyarıyı tetikleyen insider risk yönetimi ilkesi GUID'si. |
| Önem Derecesi | Uyarının önem derecesi. Değerler *Yüksek,* Orta *veya* *Düşük'tür*. |
| Kaynak | Uyarının kaynağı. Değer Güvenlik *Office 365 Uyumluluğu & olur*. |
| Durum | Uyarının durumu. Değerler *Etkindir* *(* Insider riski içinde Gözden Geçirilir *),* Araştırılıyor *(* Insider riski ile onaylandı), *Çözümlendi* *(* Insider riskiyle *çözüldü), Yok* *(* Insider riskiyle karşılandı). |
| Sürüm | Güvenlik ve uyumluluk uyarı şemasının sürümü. |

Genel şema için Insider risk yönetimi uyarıları için aşağıdaki alanlar [ve değerler Office 365 API ortak şeması için dışarı aktarıldı](/office/office-365-management-api/office-365-management-activity-api-schema#common-schema).

- UserId
- Kimlik
- RecordType
- CreationTime
- Operation
- OrganizationId
- UserType
- UserKey

## <a name="priority-user-groups-preview"></a>Öncelik kullanıcı grupları (önizleme)

Kuruluşta yer alan kullanıcıların konumlarına, hassas bilgilere erişim düzeylerine veya risk geçmişine bağlı olarak farklı risk düzeyleri olabilir. Bu kullanıcıların etkinliklerini takip etmek ve puanlamanın önceliklerini belirlemek, organizasyon açısından daha yüksek sonuçlar doğuracak olası riskler hakkında sizi uyarmanıza yardımcı olabilir. Insider risk yönetimi'nin öncelik kullanıcı grupları, daha yakın denetime ve daha hassas risk puanlamalarına ihtiyaç olan kullanıcıları tanımlamaya yardımcı olur. Öncelik kullanıcıları tarafından *güvenlik* ilkesi ihlalleri ve öncelik kullanıcıları ilke şablonlarının Veri sızıntıları ile birlikte, öncelik kullanıcı grubuna eklenen kullanıcıların daha yüksek önem düzeyine sahip insider risk uyarıları ve uyarıları olasılığı artırıldı.

![Insider risk yönetimi öncelik kullanıcı grubu ayarları.](../media/insider-risk-settings-priority-users.png)

Tüm analistler ve güvenlikçiler tarafından gözden geçir açık olmak yerine, Öncelik kullanıcı gruplarının gözden geçirme etkinliklerini belirli kullanıcılarla veya insider risk rol gruplarıyla kısıtlaması da gerekir. Her öncelikli kullanıcı grubu için kullanıcıları, uyarıları, vakaları ve raporları gözden geçirmek için tek tek kullanıcılar ve rol grupları atamayı seçebilirsiniz. Öncelik kullanıcı grupları yerleşik *Insider Risk Yönetimi, Insider Risk* Yönetimi Analistleri ve *Insider Risk* Yönetimi Tahminleri rol gruplarına, bu rol gruplarından bir veya birden fazlasına veya özel bir kullanıcı seçimine atanmış izinlere sahip olabilir. 

Örneğin, kullanıcıların hassas bilgilere erişimi olduğu çok gizli bir projede veri sızıntılarına karşı korumanız gerekir. Bu proje üzerinde *çalışan kullanıcılar Project* *için* Gizli kullanıcı grubu oluşturma Project Öncelik kullanıcı grubu. Buna ek olarak, bu öncelik kullanıcı grubunun, varsayılan insider risk yönetimi yöneticilerinin, analistlerin ve tahminlerin tüm varsayılan insider risk yönetimi yöneticileri tarafından görülebilecek kullanıcılar, uyarılar, vakalar ve raporlar olmaması gerekir. Daha **Ayarlar** için Gizli kullanıcı *Project* Kullanıcılar öncelik kullanıcıları grubunu oluşturabilir ve iki kullanıcıya, gruplarla ilgili verileri görüntüley gerçekten gözden geçirici olarak atayabilirsiniz. İlke sihirbazını ve Öncelik  kullanıcıları tarafından veri sızıntıları ilke şablonunu kullanarak, yeni bir ilke oluşturur ve Gizli *Project* Kullanıcılar öncelik kullanıcıları grubunu ilkeye atarsınız. Gizli *Project* Kullanıcıları önceliğe sahip kullanıcı grubu üyeleri için ilke tarafından inceleyen etkinlikler risklere ve bu kullanıcıların etkinliklerine daha duyarlı olur ve bu kullanıcıların bir uyarı oluşturma olasılığı daha yüksektir ve daha yüksek önem düzeyine sahip uyarılar içerirler.

### <a name="create-a-priority-user-group"></a>Öncelik kullanıcı grubu oluşturma

Yeni bir öncelik kullanıcı grubu oluşturmak için, ilgili grupta **Insider risk yönetimi** çözümünde ayar denetimlerini Microsoft 365 uyumluluk merkezi. Öncelik kullanıcı grubu oluşturmak için, *Insider Risk Yönetimi veya Insider Risk Yönetimi* Yöneticisi *rol grubunun üyesi olmalıdır* .

Öncelik kullanıcı grubu oluşturmak için aşağıdaki adımları tamamlayın:

1. Aşağıdaki [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne gidin ve** **Insider risk ayarları'ı seçin**.
2. Öncelik kullanıcı **grupları (önizleme) sayfasını** seçin.
3. Öncelik kullanıcı **grupları (önizleme) sayfasında** Öncelik kullanıcı grubu **oluştur'a seçerek** grup oluşturma sihirbazını başlatın.
4. Ad **ve açıklama sayfasında** aşağıdaki alanları doldurun:
    - **Ad (gerekli)**: Öncelik kullanıcı grubu için kolay bir ad girin. Sihirbazı tamamlandıktan sonra öncelik kullanıcı grubunun adını değiştiremezsiniz.
    - **Açıklama (isteğe bağlı)**: Öncelik kullanıcı grubu için bir açıklama girin.
5. Devam etmek **için Sonraki'yi** seçin.
6. Üye **seç sayfasında**, Aranecek üyeleri  seçin'i seçin ve posta özelliği etkin olan kullanıcı hesaplarının gruba dahil olduğunu seçin veya tüm kuruluş kullanıcıları gruba  eklemek için Tüm kullanıcıları seç onay kutusunu seçin. Gruba **kullanıcı eklemeden** devam **etmek için** Ekle'yi veya kapatmak için İptal'i seçin.
7. Devam etmek **için Sonraki'yi** seçin.
8. Bu **grubu kimlerin görüntüleyebilirsiniz?** sayfasında, öncelik kullanıcı grubu için kullanıcıları, uyarıları, vakaları ve raporları kimlerin gözden geçir geçire birini tanımlamanız gerekir. En az bir kullanıcı veya insider risk yönetimi rol grubu atanabilir. Kullanıcıları **ve rol gruplarını seçin'i** seçin ve öncelik kullanıcı grubuna atamak istediğiniz kullanıcıları veya Insider risk yönetimi rol gruplarını seçin. Seçilen **kullanıcıları** veya rol gruplarını gruba atamak için Ekle'yi seçin.
9. Devam etmek için Sonraki'yi seçin.
10. Gözden **Geçir** sayfasında, öncelik kullanıcı grubu için seçtiğiniz ayarları gözden geçirin. Grup **değerlerden herhangi** birini değiştirmek için Düzenle bağlantılarını seçin veya öncelik kullanıcı **grubunu** oluşturmak ve etkinleştirmek için Gönder'i seçin.
11. Onay sayfasında Bitti'yi **seçerek** sihirbazdan çıkın.

### <a name="update-a-priority-user-group"></a>Öncelik kullanıcı grubunu güncelleştirme

Var olan bir öncelik kullanıcı grubunu güncelleştirmek için, aşağıdaki çalışma sayfalarındaki **Insider risk yönetimi** çözümünde ayar denetimlerini Microsoft 365 uyumluluk merkezi. Öncelik kullanıcı grubunu güncelleştirmek için, *Insider Risk Yönetimi veya Insider Risk Yönetimi* Yöneticisi *rol grubunun üyesi olun* .

Öncelik kullanıcı grubunu düzenlemek için aşağıdaki adımları tamamlayın:

1. Aşağıdaki [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne gidin ve** **Insider risk ayarları'ı seçin**.
2. Öncelik kullanıcı **grupları (önizleme) sayfasını** seçin.
3. Düzenlemek istediğiniz öncelik kullanıcı grubunu ve ardından Grubu **düzenle'yi seçin**.
4. Ad ve **açıklama sayfasında** , gerekirse Açıklama alanını güncelleştirin. Öncelik kullanıcı grubunun adını güncelleştiresiniz. Devam etmek **için Sonraki'yi** seçin.
5. Üye **seç sayfasında** , Üye seç denetimlerini kullanarak gruba yeni **üyeler** ekleyin. Gruptan bir kullanıcı kaldırmak için kaldırmak istediğiniz kullanıcının yanındaki 'X' öğesini seçin. Devam etmek **için Sonraki'yi** seçin.
6. Bu grubu **kimlerin görüntüley** cases, add or remove users or role groups that can review users, alerts, cases, and reports for the priority user group.
7. Devam etmek **için Sonraki'yi** seçin.
8. Gözden **Geçir** sayfasında, öncelik kullanıcı grubu için seçtiğiniz güncelleştirme ayarlarını gözden geçirebilirsiniz. Grup **değerlerden** herhangi birini değiştirmek için Düzenle bağlantılarını seçin veya öncelik kullanıcı **grubunu** güncelleştirmek için Gönder'i seçin.
9. Onay sayfasında Bitti'yi **seçerek** sihirbazdan çıkın.

### <a name="delete-a-priority-user-group"></a>Öncelik kullanıcı grubunu silme

Var olan bir öncelik kullanıcı grubunu silmek için, ilgili grupta **insider risk yönetimi** çözümünde ayar denetimlerini Microsoft 365 uyumluluk merkezi. Öncelik kullanıcı grubunu silmek için, *Insider Risk Yönetimi veya Insider Risk Yönetimi* Yöneticisi *rol grubunun üyesi olmak* gerekir.

> [!IMPORTANT]
> Öncelik kullanıcı grubunun silinmesi, atandığı tüm etkin ilkelerden kaldırır. Etkin bir ilkeye atanmış olan öncelik kullanıcı grubunu silerseniz, ilke kapsam içinde hiçbir kullanıcı içermez ve etkin bir şekilde boşta olur ve uyarı oluşturmaz.

Öncelik kullanıcı grubunu silmek için aşağıdaki adımları tamamlayın:

1. Aşağıdaki [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne gidin ve** **Insider risk ayarları'ı seçin**.
2. Öncelik kullanıcı **grupları (önizleme) sayfasını** seçin.
3. Düzenlemek istediğiniz öncelik kullanıcı grubunu seçin ve pano **menüsünden Sil'i** seçin.
4. Sil iletişim **kutusunda** , öncelik kullanıcı **grubunu silmek** için Evet'i veya panoya dönmek **için** İptal'i seçin.

## <a name="priority-physical-assets-preview"></a>Öncelikli fiziksel varlıklar (önizleme)

Öncelikli fiziksel varlıklara erişimi belirlemek ve erişim etkinliğini kullanıcı olaylarıyla ilişkili olarak belirlemek, uyumluluk altyapınız için önemli bir bileşendir. Bu fiziksel varlıklar, şirket binaları, veri merkezleri veya sunucu odaları gibi, organizasyonda öncelik konumlarını temsil ediyor. Insider risk etkinlikleri alışılmışın dışında çalışan kullanıcılarla, bu yetkisiz hassas veya güvenli alanlara erişme girişiminde bulunan kullanıcılarla ve yasal olmayan ihtiyaçlar olmadan üst düzey bölgelere erişim istekleriyle ilişkilendirilebilirsiniz.

Öncelikli fiziksel varlıklar etkinleştirildiğinde ve Fiziksel [](import-physical-badging-data.md) sertifikalar veri bağlayıcısı yapılandırıldığında, Insider risk yönetimi fiziksel denetim ve erişim sistemlerinizin sinyallerini diğer kullanıcı risk etkinlikleriyle tümleştirir. Fiziksel erişim sistemleri genelinde davranışın desenlerini inceleerek ve bu etkinlikleri diğer Insider risk olaylarıyla uyumlu hale getirerek, insider risk yönetimi uyarılara daha bilinçli yanıt kararları alacaktır. Öncelikli fiziksel varlıklara erişim, önceliksiz varlıklara erişimden farklı şekilde puanlandı ve öngörülerde tanımlanır.

Örneğin, kuruluşta, normal çalışma alanlarına ve hassas proje alanlarına fiziksel erişimi izleyen ve onaylayan kullanıcılar için bir belgeleme sistemi vardır. Hassas bir proje üzerinde birkaç kullanıcınız çalışıyor ve bu kullanıcılar proje tamamlandığında kuruluşun diğer alanlarına geri dönecektir. Hassas proje tamamlanmaya yaklaş yakınında olduğundan, proje çalışmalarının gizli kalmasını ve proje alanlarına erişimin sıkı bir denetim altında tutul olduğundan emin olmak istiyorsunuz.

Fiziksel bajman veri bağlayıcısı'nın, Microsoft 365 badging sisteminiz üzerinden erişim bilgilerini içeri aktarması ve Insider risk yönetiminde öncelik fiziksel varlıklarını belirtmeyi seçebilirsiniz. Lisanslama sisteminiz üzerinden bilgileri içeri aktararak ve fiziksel erişim bilgilerini Insider risk yönetiminde tanımlanan diğer risk etkinlikleriyle bağlantılı bir şekilde gerçekleştirerek, proje kullanıcılarından birinin normal çalışma saatlerinden sonra proje ofislerine eriştiklerini ve ayrıca büyük miktarda verileri kendi normal çalışma yerlerinden kişisel bir bulut depolama hizmetine aktarıyor olduğunu fark ettiysiniz. Çevrimiçi etkinlikle ilişkili bu fiziksel erişim etkinliği, olası veri hırsızlığına ve uyumluluklarına ve analistlere, bu kullanıcının durumlarının belirlediklerine uygun eylemler gerçekleştirelerine işaret ediyor olabilir.

![Insider risk yönetimi önceliği fiziksel varlıklar.](../media/insider-risk-settings-priority-assets.png)

### <a name="configure-priority-physical-assets"></a>Öncelikli fiziksel varlıkları yapılandırma

Öncelikli fiziksel varlıkları yapılandırmak için Fiziksel bajman bağlayıcısı yapılandırarak ilgili çözümde **Insider risk yönetimi** çözümünde ayar denetimlerini Microsoft 365 uyumluluk merkezi. Öncelikli fiziksel varlıkları yapılandırmak için Insider Risk Yönetimi veya *Insider Risk Yönetimi* Yöneticisi *rol grubunun üyesi olmak gerekir*.

Öncelikli fiziksel varlıkları yapılandırmak için aşağıdaki adımları tamamlayın:

1. Insider risk yönetimiyle çalışmaya başlama makalesinde [Insider risk yönetimi için yapılandırma adımlarını](insider-risk-management-configure.md) izleyin. 3. Adım'da Fiziksel bağlantı bağlayıcısı'nın yapılandırıldığından emin olun.

    > [!IMPORTANT]
    > Insider risk yönetimi ilkelerinin fiziksel kontrol ve erişim platformlardan etkinlik verileriyle ayrılan ve sonlandırılan kullanıcılarla ilgili sinyal verilerini kullanması ve bu verileri birbiriyle bağlantılı olarak birbiriyle bağlantılı kılabilir olması için, İk bağlayıcısını Microsoft 365 yapılandırmanız gerekir. Fiziksel badging bağlayıcısını Microsoft 365 HR bağlayıcısını etkinleştirmeden etkinleştirirsiniz, insider risk yönetimi ilkeleri yalnızca organizasyonlu kullanıcılar için fiziksel erişim etkinlikleri için olayları işler.

2. Aşağıdaki [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne gidin ve** **Insider risk ayarlarıYazdırma** >  **fiziksel varlıklar'ı seçin**.
3. Öncelikli fiziksel  varlıklar sayfasında, Fiziksel belgeleme bağlayıcısı tarafından içeri aktarılan varlık olaylarını izlemek istediğiniz fiziksel varlık kimliklerini el ile ekleyebilir veya Fiziksel kimlik bağlayıcısı tarafından içeri aktarılan tüm fiziksel varlık kimliklerinin .csv dosyasını içeri aktarabilirsiniz: a) Fiziksel varlık kimliklerini el ile eklemek için, Öncelik fiziksel varlıkları ekle'yi **seçin.**  bir fiziksel varlık kimliği girin, ardından Ekle'yi **seçin**. Diğer fiziksel varlık kimliklerini girin ve girilen tüm varlıkları **kaydetmek için Öncelik** fiziksel varlık ekle'yi seçin.
    b) Bir dosyadan fiziksel varlık kimliklerinin listesini eklemek için .csv önceliğe ait fiziksel varlıkları **içeri aktar'ı seçin**. Dosya Gezgini iletişim kutusunda, içeri .csv istediğiniz dosyanın adını seçin ve sonra da Aç'ı **seçin**. Dosyalardan gelen fiziksel .csv kimlikleri listeye eklenir.
4. Çalışma sayfasında **İlke göstergeleri** sayfasına **Ayarlar**.
5. İlke **göstergeleri sayfasında** , Fiziksel erişim göstergeleri bölümüne gidin ve **Fesih** sonrasında fiziksel erişim veya hassas varlığa erişim başarısız oldu onay **kutusunu seçin**.
6. Yapılandırmak **ve çıkmak** için Kaydet'i seçin.

### <a name="delete-a-priority-physical-asset"></a>Öncelikli fiziksel varlığı silme

Mevcut öncelikli bir fiziksel varlığı silmek için, ilgili kaynakta bulunan Insider risk yönetimi çözümünde ayar denetimlerini Microsoft 365 uyumluluk merkezi. Öncelikli bir fiziksel varlığı silmek için Insider Risk Yönetimi veya Insider Risk Yönetimi Yöneticisi rol grubunun üyesi olmak gerekir.

> [!IMPORTANT]
> Öncelikli fiziksel varlık silinerek, daha önce dahil edilen herhangi bir etkin ilke tarafından onaytan kaldırılan bir varlık daha önce dahil edilir. Öncelikli fiziksel varlıkla ilişkilendirilmiş etkinlikler tarafından oluşturulan uyarılar silinmez.

Öncelikli bir fiziksel varlığı silmek için aşağıdaki adımları tamamlayın:

1. Aşağıdaki [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne gidin ve** **Insider risk ayarlarıYazdırma** >  **fiziksel varlıklar'ı seçin**.
2. Öncelikli **fiziksel varlıklar sayfasında** , silmek istediğiniz varlığı seçin.
3. Varlığı **silmek** için eylem menüsünde Sil'i seçin.

## <a name="power-automate-flows-preview"></a>Power Automate akışları (önizleme)

[Microsoft Power Automate](/power-automate/getting-started), uygulamalar ve hizmetler genelinde eylemleri otomatik haleleştiren bir iş akışı hizmetidir. Şablonlardan gelen akışları kullanarak veya el ile oluşturulan bunları kullanarak, bu uygulama ve hizmetlerle ilişkili genel görevleri otomatik haleebilirsiniz. Insider risk Power Automate için kullanıcı akışlarını etkinleştirebilir, vakalar ve kullanıcılar için önemli görevleri otomatik hale getirebilirsiniz. Kullanıcı, uyarı Power Automate olay bilgilerini almak, bu bilgileri proje katılımcıları ve diğer uygulamalarla paylaşmak, ayrıca Insider risk yönetiminde vaka notlarını gönderme gibi eylemleri otomatikleştirmek için akış akışlarını yapılandırabilirsiniz. Power Automate akışları durumlar ve ilke kapsamındaki tüm kullanıcılar için geçerlidir.

Insider risk Microsoft 365 içeren veya insider risk yönetimi içeren Power Automate ve önerilen insider risk yönetimini ve şablonlarını kullanmak için ek Power Automate ihtiyacı yoktur. Bu şablonlar, organizasyonlarınızı destekleyecek şekilde özelleştirilebilir ve temel Insider risk yönetimi senaryolarını kapsıyor olabilir. Bu şablonlarda premium Power Automate özelliklerini kullanmayı seçerseniz, Microsoft 365 uyumluluk bağlayıcısını kullanarak özel bir şablon oluşturun veya Microsoft 365'daki diğer uyumluluk alanları için Power Automate şablonlarını kullanırsanız daha fazla lisansa Power Automate ihtiyacınız olabilir.

Aşağıdaki Power Automate, insider risk yönetimi kullanıcıları ve durumlarının süreç otomasyonunu desteklemesi için müşterilere sağlanır:

- **Insider risk** ilkesine eklenen kullanıcıları bilgilendirin: Bu şablon, insider risk yönetimi ilkelerine tabi olan kullanıcılara bildirilecek iç ilkeleri, gizliliği veya yasal düzenleme gereksinimleri olan kuruluşlara yöneliktir. Bu akış Kullanıcılar sayfasında bir kullanıcı için yapılandırıldığında ve seçildiğinde, kullanıcı  insider risk yönetimi ilkesine ekli olduğunda kullanıcılara ve yöneticilerine bir e-posta iletisi gönderilir. Bu şablon aynı zamanda tarih/saat SharePoint ileti alıcısı gibi bildirim iletisi ayrıntılarının SharePoint için bir sitede barındırılan liste listesinin güncelleştirilsini de destekler. Gizlilik ayarlarında kullanıcıları anonimleştirmeyi seçtiysiniz **, bu** şablondan oluşturulan akışlar kullanıcı gizliliğinin korunması için amaçlanan şekilde çalışmaz. Power Automate şablon kullanan diğer akışlara Kullanıcılar **panosundan da görebilirsiniz**.
- İk veya işletmeden **, insider risk** durumundaki bir kullanıcı hakkında bilgi talep edin: Bir vakaya göre hareket etmek için insider risk analistleri ve ekiplerin durum etkinliklerinin bağlamını anlamak için İk'ya veya diğer paydaşlara danışması gerekir. Bu akış bir olay için yapılandırıldığında ve seçildiğinde, analistler ve tahminler bu akış için yapılandırılmış İk ve iş paydaşlarına bir e-posta iletisi gönderir. Her alıcıya önceden yapılandırılmış veya özelleştirilebilir yanıt seçenekleri olan bir ileti gönderilir. Alıcılar bir yanıt seçeneği belirliyken, yanıt büyük/küçük harf notu olarak kaydedilir ve alıcı ve tarih/saat bilgilerini içerir. Gizlilik ayarlarında kullanıcıları anonimleştirmeyi seçtiysiniz **, bu** şablondan oluşturulan akışlar kullanıcı gizliliğinin korunması için amaçlanan şekilde çalışmaz. Power Automate şablon kullanan diğer akışlara Cases **panosundan da sknz.**
- **Bir kullanıcının insider risk uyarısı** olduğunda yöneticiye durumu bildir: Bazı kuruluşların, kullanıcıda insider risk yönetimi uyarısı olduğunda hemen yönetim uyarısı verilmesi gerekiyor olabilir. Bu akış yapılandırıldığında ve seçildiğinde, olay yöneticisine tüm olay uyarıları hakkında aşağıdaki bilgileri içeren bir e-posta iletisi gönderilir:
    - Uyarı için geçerli ilke
    - Uyarının Tarihi/Saati
    - Uyarının önem düzeyi

    Akış, iletinin gönderildiği ve akışın etkinleştirildiğinde olay notlarını otomatik olarak ler. Gizlilik ayarlarında kullanıcıları anonimleştirmeyi seçtiysiniz **, bu** şablondan oluşturulan akışlar kullanıcı gizliliğinin korunması için amaçlanan şekilde çalışmaz. Power Automate şablon kullanan diğer akışlara Cases **panosundan da sknz.**
- **ServiceNow'da Insider risk** durumu için kayıt oluşturun: Bu şablon, Insider risk yönetimi durumlarını izlemek için ServiceNow çözümlerini kullanmak isteyen kuruluşlara aittir.  Böyle bir durumda, Insider risk analistleri ve tahminler ServiceNow'da vaka için bir kayıt oluşturabilir. Bu şablonu, ServiceNow'da seçilen alanları kurum gereksinimlerine göre doldurmak için özelleştirebilirsiniz. Power Automate şablon kullanan diğer akışlara Cases **panosundan da sknz.** Kullanılabilir ServiceNow alanları hakkında daha fazla bilgi için [ServiceNow Bağlayıcısı başvuru makalesine](/connectors/service-now/) bakın.

### <a name="create-a-power-automate-flow-from-insider-risk-management-template"></a>Insider risk Power Automate şablonundan iş akışı oluşturma

Önerilen bir Insider risk yönetimi şablonundan Power Automate akışı oluşturmak için, Microsoft 365 uyumluluk merkezi'te **Insider risk** yönetimi çözümünde veya doğrudan Üzerinde çalışırken otomatik denetimden **gelen Power Automate** akışlarını yönet seçeneğini kullanırsınız. **Vakalar** **veya Kullanıcılar panoları**.

Ayarlar alanında Power Automate akışı oluşturmak için *, Insider Risk Yönetimi* veya *Insider Risk Yönetimi* Yöneticisi rol grubunun üyesi olun. Proje akışlarını Power Automate ile bir **Power Automate akışı** oluşturmak için, en az bir insider risk yönetimi rol grubunun üyesi olmak gerekir.

Önerilen insider risk yönetimi şablonundan Power Automate akışı oluşturmak için aşağıdaki adımları tamamlayın:

1. Aşağıdaki [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne gidin ve** **Insider risk ayarları'Power Automate** >  **seçin**. Ayrıca, ServisLer veya Kullanıcılar **pano sayfalarından****,** Akış akışlarını **otomatik olarak** >  **Power Automate edebilirsiniz**.
2. Sayfa **Power Automate sayfasında**, beğendiğiniz **Insider risk yönetimi şablonları bölümünden** önerilen bir şablonu seçin.
3. Akış, akış için gereken ekli bağlantıları listeler ve bağlantı durumlarının olup olduğunu not eder. Gerekirse, kullanılabilir durumda görüntülenmeen tüm bağlantıları güncelleştirin. **Devam'ı seçin**.
4. Varsayılan olarak, önerilen akışlar önerilen insider risk yönetimi ve akış için atanan görevi tamamlamak için Microsoft 365 veri alanlarıyla önceden yapılandırılmıştır. Gerekirse, Gelişmiş seçenekleri göster denetimlerini kullanarak ve **akış bileşeni** için kullanılabilir özellikleri yapılandırarak akış bileşenlerini özelleştirin.
5. Gerekirse, Yeni adım düğmesini seçerek akışa başka **adımlar ekleyin** . Çoğu durumda, önerilen varsayılan şablonlar için bu gerekli olmaması gerekir.
6. Akışı **daha ileri bir** yapılandırma için kaydetmek için Taslağı kaydet'i veya **akışın** yapılandırmasını tamamlamak için Kaydet'i seçin.
7. Akış **akışı** sayfasına dönmek için **Power Automate seçin**. Yeni şablon, Akışlarım sekmelerinde akış olarak listelenir ve  akışı oluşturan kullanıcı için Insider risk yönetimi durumlarında çalışırken otomatik olarak Otomatik açılır denetiminden kullanılabilir.

> [!IMPORTANT]
> Akışın, organizasyon daki diğer kullanıcıların akışa erişimi olması gerekirse, akışın paylaşılıyor olması gerekir.

### <a name="create-a-custom-power-automate-flow-for-insider-risk-management"></a>Insider risk Power Automate için özel görev akışı oluşturma

Bazı süreçler ve kuruluşları için iş akışları önerilen insider risk yönetimi akış şablonlarının dışında olabilir ve insider risk yönetim alanları için özel Power Automate akışları oluşturmanız gerekiyor olabilir. Power Automate esnek ve desteklenen kapsamlı özelleştirmelerdir, ancak Insider risk yönetimi özellikleriyle tümleştirilmesi için atılması gereken adımlar vardır.

Insider risk yönetimine özel bir Power Automate şablonu oluşturmak için aşağıdaki adımları tamamlayın:

1. **Power Automate akışı lisansınızı** kontrol edin: Insider risk yönetimi tetikleyicilerini kullanan Power Automate akışlar oluşturmak için, Power Automate gerekir. Önerilen Insider risk yönetimi akış şablonları ek lisans gerektirmez ve Insider risk yönetimi lisansınız kapsamında yer almaktadır.
2. **Otomatik akış oluşturma**: Bir insider risk yönetimi olayı tarafından tetiklendiğinde bir veya birden çok görev gerçekleştiren bir akış oluşturun. Otomatik akış oluşturma hakkında ayrıntılı bilgi için bkz. [Power Automate.](/power-automate/get-started-logic-flow)
3. **Uyumluluk Microsoft 365 seçin: Uyumluluk** bağlayıcısı için arama Microsoft 365 seçin. Bu bağlayıcı, Insider risk yönetimi tetikleyicilerini ve eylemlerini sağlar. Bağlayıcılar hakkında daha fazla bilgi için Bağlayıcı başvurusuna [genel bakış makalesine](/connectors/connector-reference/) bakın.
4. **Akışınız için insider risk yönetimi tetikleyicilerini seçin**: Insider risk yönetiminin özel risk yönetimi için iki Power Automate vardır:
    - **Seçili bir insider risk yönetimi durumu için**: Bu tetikleyiciye sahip akışlar, Insider risk yönetimi Durumlar pano sayfasından seçilebilir.
    - **Seçili bir insider risk yönetimi kullanıcısı için**: Bu tetikleyiciye sahip akışlar, Insider risk yönetimi Kullanıcılar pano sayfasından seçilebilir.
5. Akışınız için insider risk yönetimi eylemlerini seçin: Insider risk yönetiminin özel akışınıza dahil etmek üzere çeşitli eylemlerinden birini seçebilirsiniz:
    - Insider risk yönetimi uyarısı al
    - Insider risk yönetimi durumuna al
    - Insider risk yönetimi kullanıcısı al
    - Bir davayla ilgili insider risk yönetimi uyarıları al
    - Insider risk yönetimi vaka notu ekleme

### <a name="share-a-power-automate-flow"></a>Akış Power Automate paylaşma

Varsayılan olarak Power Automate oluşturduğu akışlara yalnızca o kullanıcı tarafından kullanılabilir. Diğer Insider risk yönetimi kullanıcılarının akışa erişimi ve akış kullanmaları için, akışı oluşturan kişi tarafından paylaşılıyor olması gerekir. Bir akışı paylaşmak için, doğrudan Vakalar veya Kullanıcılar pano sayfalarında çalışırken Otomatik denetimden gelen Microsoft 365 uyumluluk merkezi veya **Power Automate** akışlarını yönet seçeneğinde **Insider risk** yönetimi çözümünün ayarlar denetimlerini kullanacağız.  Bir akışı paylaştıktan sonra, akışla paylaşılan herkes Olay ve Kullanıcı panolarında yer alan Otomatik denetim açılan listesinde  **akışa erişebilirsiniz**.

Ayarlar alanında Power Automate akışı paylaşmak için *, Insider Risk Yönetimi* veya *Insider Risk Yönetimi* Yöneticisi rol grubunun üyesi olun. Bir grup Power Automate Akışlarını yönet **Power Automate paylaşmak** için, en az bir insider risk yönetimi rol grubunun üyesi olmak gerekir.

Veri akışı paylaşmak için aşağıdaki Power Automate tamamlayın:

1. Aşağıdaki [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne gidin ve** **Insider risk ayarları'Power Automate** >  **seçin**. Ayrıca, ServisLer veya Kullanıcılar **pano sayfalarından****,** Akış akışlarını **otomatik olarak** >  **Power Automate edebilirsiniz**.
2. Akış **Power Automate,** Akışlarım **veya Ekip akışları** **sekmesini** seçin.
3. Paylaşacak akışı seçin ve ardından akış seçenekleri **menüsünden** Paylaş'ı seçin.
4. Akış paylaşımı sayfasında, akış için sahip olarak eklemek istediğiniz kullanıcının veya grubun adını girin.
5. Bağlantı Kullanıldı **iletişim kutusunda** , eklenen **kullanıcının veya grubun** akışa tam erişime sahip olduğunu kabul etmek için Tamam'ı seçin.

### <a name="edit-a-power-automate-flow"></a>Akış Power Automate düzenleme

Bir akışı düzenlemek için, doğrudan Vakalar veya Kullanıcılar panolarında çalışırken Otomatik denetimden gelen Microsoft 365 uyumluluk merkezi veya **Power Automate** akışlarını yönet seçeneğinde **Insider risk** yönetimi çözümünün ayarlar denetimlerini  kullanırsiniz **.**

Ayarlar alanında Power Automate akışı düzenlemek için *, Insider Risk Yönetimi* veya *Insider Risk Yönetimi* Yöneticisi rol grubunun üyesi olun. Bir grup Power Automate Akışlarını yönet **seçeneğiyle Power Automate** için, en az bir insider risk yönetimi rol grubunun üyesi olmak gerekir.

Bir veri akışını düzenlemek için aşağıdaki Power Automate tamamlayın:

1. Aşağıdaki [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne gidin ve** **Insider risk ayarları'Power Automate** >  **seçin**. Ayrıca, ServisLer veya Kullanıcılar **pano sayfalarından****,** Akış akışlarını **otomatik olarak** >  **Power Automate edebilirsiniz**.
2. Akış **Power Automate, düzenlemek** için bir akış seçin ve akış denetimi **menüsünden Düzenle'yi** seçin.
3. Akış bileşeni **Ayarlar** >  **değiştirmek için** üç noktayı veya akış bileşenini **silmek** >  için üç noktayı seçin.
4. Akışı **düzenlemeyi** tamamlamak için **Kaydet'i** ve sonra Kapat'ı seçin.

### <a name="delete-a-power-automate-flow"></a>Bir Power Automate silme

Bir akışı silmek için, doğrudan Vakalar veya Kullanıcılar panolarında çalışırken Otomatik denetimden gelen Microsoft 365 uyumluluk merkezi veya **Power Automate** akışlarını yönet seçeneğinde **Insider risk** yönetimi çözümünün ayarlar denetimlerini  kullanırsiniz **.** Akış silindiğinde, tüm kullanıcılar için bir seçenek olarak kaldırılır.

Ayarlar alanında Power Automate akışı silmek için *, Insider Risk Yönetimi* veya *Insider Risk Yönetimi* Yöneticisi rol grubunun üyesi olun. Veri akışlarını Power Automate akışlarını yönet **Power Automate** bir kullanıcı akışını silmek için, en az bir insider risk yönetimi rol grubunun üyesi olmak gerekir.

Veri akışı silmek için aşağıdaki Power Automate tamamlayın:

1. Aşağıdaki [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne gidin ve** **Insider risk ayarları'Power Automate** >  **seçin**. Ayrıca, ServisLer veya Kullanıcılar **pano sayfalarından****,** Akış akışlarını **otomatik olarak** >  **Power Automate edebilirsiniz**.
2. Akış **Power Automate, silmek** için bir akış seçin ve akış denetimi **menüsünden Sil'i** seçin.
3. Silme onayı iletişim kutusunda, akışı kaldırmak **için Sil'i** veya silme eylemden **çıkmak için** İptal'i seçin.

## <a name="microsoft-teams-preview"></a>Microsoft Teams (önizleme)

Uyumluluk analistleri ve tahminler, Insider risk Microsoft Teams durumlarında işbirliği için kolayca uyumluluk tekniklerini kullanabilir. Diğer proje katılımcılarının eşgüdüm ve iletişim kurarak şunları Microsoft Teams:

- Özel kanallarda vakalar için yanıt etkinliklerini koordine Teams gözden geçirme
- Tek tek vakalarla ilgili dosyaları ve kanıtı güvenli bir şekilde paylaşma ve depolama
- Analistlere ve tahminlere göre yanıt etkinliklerini izleme ve gözden geçirme

Insider Microsoft Teams için etkinleştirildikten sonra, her uyarı onaylandıktan ve bir olay oluşturulduğunda Microsoft Teams bir ekip oluşturulur. Ekip varsayılan olarak, *otomatik olarak Insider Risk Yönetimi*, *Insider Risk* Yönetimi Analistleri ve *Insider Risk Yönetimi* Güvenlikçileri rol gruplarının (100'e kadar ilk kullanıcıya kadar) üyelerini içerir. Kuruluş katkıda bulunan diğer katılımcılar, oluşturulduktan ve uygun olduğunda eklenmiştir. Yeni iş Microsoft Teams önceden oluşturulan mevcut vakalar için, analistler ve tahminler gerekirse bir dava üzerinde çalışırken yeni Microsoft Teams bir ekip oluşturmayı seçebilirler.  Insider risk yönetiminde ilişkili durumu çöztüklerinden, ekip otomatik olarak arşivlenir (gizli ve salt okunur olarak taşınır).

Aynı ekiplerde ekipleri ve kanalları kullanma hakkında daha fazla bilgi için Microsoft Teams'de [ekiplere ve kanallara genel Microsoft Teams](/MicrosoftTeams/teams-channels-overview).

Durumlar Microsoft Teams desteğinin etkinleştirilmesi hızlı ve kolay bir yapılandırmadır. Insider risk Microsoft Teams en iyi şekilde etkinleştirmek için aşağıdaki adımları tamamlayın:

1. Aşağıdaki [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimiInsider** >  **risk ayarları'ne gidin**.
2. Sayfayı **Microsoft Teams** seçin.
3. Insider risk Microsoft Teams için proje tümleştirmeyi etkinleştirin.
4. Yapılandırmak **ve çıkmak** için Kaydet'i seçin.

![Insider risk yönetimi Microsoft Teams.](../media/insider-risk-settings-teams.png)

### <a name="create-a-microsoft-teams-team-for-existing-cases"></a>Mevcut Microsoft Teams bir ekip oluşturma

Mevcut durumlar Microsoft Teams Insider risk yönetimi için insider desteği sağlarsanız, her dava için el ile gerektiğinde bir ekip oluşturmanız gerekir. Insider risk Microsoft Teams ayarlarına bu desteği etkinleştirdikten sonra, yeni vakalar otomatik olarak yeni bir ekip Microsoft Teams oluşturulur.

Kullanıcıların, bir vakadan Microsoft 365 ekip oluşturmak için, Microsoft Teams grupları oluşturma iznine ihtiyacı vardır. Grupların izinlerini yönetme hakkında daha fazla Microsoft 365 için bkz[. Gruplarda kimlerin Microsoft 365 yönetme](../solutions/manage-creation-of-groups.md).

Bir dava için ekip oluşturmak üzere, mevcut bir vakada doğrudan çalışırken Microsoft Team Oluştur denetimlerini kullanırsanız. Yeni ekip oluşturmak için aşağıdaki adımları tamamlayın:

1. Aşağıdaki [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk** **yönetimiCases seçeneğine** >  gidin ve mevcut bir vakayı seçin.
2. Olay eylemi menüsünde **Microsoft Team Oluştur'u seçin**.
3. Ekip **adı alanına**, yeni ekip için bir ad Microsoft Teams girin.
4. **Microsoft ekibi oluştur'u ve** sonra Kapat'ı **seçin**.

Insider risk yönetimi rol gruplarına atanan kullanıcıların sayısına bağlı olarak, tüm analistlerin ve analistlerin olayla ilgili olarak Microsoft Teams bir ekipte yer almaları 15 dakika sürebilir.

## <a name="analytics"></a>Analiz

Insider risk analizi, insider risk ilkelerini yapılandırmadan, organizasyonumda olası insider risklerini değerlendirmenizi sağlar. Bu değerlendirme, kuruluşa daha yüksek kullanıcı riski olan olası alanları belirlemede yardımcı olabilir ve yapılandırmayı göz önünde bulundurarak göz önünde bulundurarak, insider risk yönetimi ilkelerinin türünü ve kapsamını belirlemeye yardımcı olabilir. Analiz taramaları, organizasyonunız için aşağıdaki avantajları sunar:

- Kolayca yapılandırabilirsiniz: Analiz taramaları ile çalışmaya başlamanız için analiz önerisinde istendiğinde Taramayı çalıştır'ı seçebilirsiniz veya **Insider risk** **ayarlarıAnalytics'ne** >  gidip analizi etkinleştirebilirsiniz.
- Tasarıma göre gizlilik: Tarama sonuçları ve içgörüler, toplu ve anonimleştirilmiş kullanıcı etkinliği olarak döndürülür; tek tek kullanıcı adları gözden geçirenler tarafından tanınmaz.
- Birleştirilmiş öngörüler aracılığıyla olası riskleri anlama: Tarama sonuçları kullanıcılarınız için olası risk alanlarını hızla tanımlamanıza yardımcı olabilir ve bu riskleri azaltmak için en iyi ilke hangisi olabilir?

Analizin olası Insider risklerini daha hızlı şekilde belirlemeye nasıl yardımcı olduğunu anlamanıza ve hızlı bir işlemde size yardımcı olan [Insider Risk Management Analytics](https://www.youtube.com/watch?v=5c0P5MCXNXk) videosunu izleyin.

Analizler, olası risk alanlarıyla ilgili içgörüleri belirlemeye yardımcı olmak için çeşitli kaynaklardan risk etkinliği etkinliklerini tarar. Geçerli yapılandırmanıza bağlı olarak, çözümleme aşağıdaki alanlarda uygun risk etkinlikleri için bilgi sağlar:

- **Microsoft 365 günlükleri görüntüleme**: Tüm taramalara dahil edilen bu kaynak, riskli olabilecek etkinliklerin çoğunu tanımlamak için birincil kaynaktır.
- **Exchange Online**: Tüm taramalara dahil edilen etkinlik Exchange Online etkinlikleri, eklerde verilerin dış kişiler veya hizmetlere e-posta ile gönder haberleri olduğunu belirlemeye yardımcı olur.
- **Azure Active Directory**: Tüm taramalara dahil edilen Azure Active Directory geçmişi, silinen kullanıcı hesaplarıyla ilişkilendirilmiş riskli etkinlikleri belirlemeye yardımcı olur.
- **Microsoft 365 İk veri** bağlayıcısı bağlayıcısı: Yapılandırılırsa, İk bağlayıcısı etkinlikleri devam veya yaklaşan sonlandırma tarihlerine sahip kullanıcılarla ilişkilendirilmiş riskli etkinlikleri belirlemeye yardımcı olur.

Taramalardan alınan çözümleme içgörüleri, Insider risk yönetimi ilkeleri tarafından kullanılan aynı risk etkinliği sinyallerine ve hem tek hem de sıralı kullanıcı etkinliklerine dayalı sonuçları raporlamaya dayalıdır. Ancak, analiz için risk puanlama etkinliği 10 günlük aktiviteye dayandırırken Insider risk ilkeleri içgörüler için günlük etkinliği kullanır. Kurumda analizi ilk kez etkinleştirtiğinde ve çalıştırarak, bir gün boyunca tarama sonuçlarını elde edin. Analizi etkin bırakırsanız, önceki 10 günlük etkinlik aralığından daha uzun bir süre için içgörü raporlarına her günlük taramanın sonuçlarının ekli olduğunu görüyorsunuz.

### <a name="enable-analytics-and-start-your-scan"></a>Analizi etkinleştirme ve taramanızı başlatma

Insider risk analizini etkinleştirmek için *Insider Risk Yönetimi'ne, Insider Risk Yönetimi* Yöneticisi'ne veya Genel Microsoft 365 rol grubuna *üye* o gerekir. 
Insider risk analizini etkinleştirmek için aşağıdaki adımları tamamlayın:

1. Aşağıdaki [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne gidin**.
2. **Insider risk** yönetimine **genel bakış sekmesinde, kuruluş kartınızda insider** risklerini tara seçeneğinde Taramayı **çalıştır'ı** seçin. Bu da, kurum için analiz taramasını kullanır. Ayrıca, **Insider risk** >  ayarlarına giderek ve Kiracınız **kullanıcı etkinliğini tarayın özelliğini** etkinleştirerek olası Insider risklerini tanım kullanarak, organizasyonda taramayı açabilirsiniz.
3. Analiz ayrıntıları **bölmesinde Taramayı** **çalıştır'ı seçerek** , kurum için taramayı başlatabilirsiniz. İncelemelerin rapor olarak gözden geçirilmeden önce analiz tarama sonuçları 48 saat kadar sürebilir.

![Insider risk yönetimi analizi ayarları.](../media/insider-risk-settings-analytics-enable.png)

### <a name="viewing-analytics-insights-and-creating-new-policies"></a>Çözümleme içgörülerini görüntüleme ve yeni ilkeler oluşturma

İşletmeniz için ilk analiz taraması tamamlandıktan sonra *Insider Risk Yönetimi* Yönetici rol grubunun üyeleri otomatik olarak bir e-posta bildirimi alırlar ve kullanıcılarınız tarafından risk altında olabilecek etkinliklere yönelik ilk öngörüleri ve önerileri görebilirsiniz. Siz organizasyonun analizini kapatmadıkça günlük taramalar devam eder. Yöneticilere e-posta bildirimleri, kuruluşta ilk etkinlik örneğinden sonra çözümlemeler (veri sızıntıları, hırsızlık ve içeriyı gönderme) için üç kapsam içi kategorinin her biri için sağlanır. Günlük taramalar sonucunda elde edilen izleme etkinliği algılaması için yöneticilere e-posta bildirimleri gönderilmez. **Insider risk** >  yönetiminde **çözümlemeler varsa Ayarlar** >  **Analytics** devre dışı bırakılır ve daha sonra organizasyonda yeniden etkinleştirilir, otomatik e-posta bildirimleri sıfırlanır ve yeni tarama öngörüleri için *Insider Risk Management Admin rol* grubunun üyelerine e-postalar gönderilir.

Organizasyonunız için olası riskleri görüntülemek için Genel Bakış sekmesine **gidin** ve Insider risk **analizi** kartında **Sonuçları görüntüle'yi** seçin. Kuruma tarama işlemi tamamlanmadı ise taramanın hala etkin olduğunu haber verilsin.

![Insider risk yönetimi analizi raporu hazır kartı.](../media/insider-risk-analytics-ready-card.png)

Tamamlanmış taramalar için, kuruluşta keşfedilen olası riskleri ve bu risklere yönelik öngörüler ve öneriler görebilirsiniz. Tanımlanan riskler ve belirli içgörüler alana göre gruplu raporlara, tanımlanan risklere sahip toplam kullanıcı sayısına, bu kullanıcıların olası riskli etkinliklere sahip yüzdesini ve bu riskleri azaltmak için önerilen bir insider risk ilkesine göre gruptur. Raporlar şunları içerir:

- **Veri sızıntıları içgörüleri**: Tüm kullanıcılar için, kuruluş dışından bilgilerin yanlışlıkla zararını veya kötü amaçlı kullanıcılar tarafından veri sızıntıları içermesi gibi etkinlikler.
- **Veri hırsızlığı içgörüleri**: Silinmiş kullanıcı veya kullanıcılarla ayrılan Azure Active Directory, kuruluş dışında risk altında bilgi paylaşımını veya kötü niyetli amacı olan kullanıcılar tarafından veri hırsızlığını içeren etkinlikler.
- **En çok yapılan bilgiler**: Tüm kullanıcıların kuruluş dışında veri paylaşımını da içeren etkinlikleri.

![Insider risk yönetimi analizine genel bakış raporu.](../media/insider-risk-analytics-overview.png)

Bir içgörüyle ilgili daha fazla bilgi görüntülemek için, **Ayrıntıları** görüntüle'yi seçerek içgörüye ilişkin ayrıntılar bölmesini görüntüleyin. Ayrıntılar bölmesi eksiksiz içgörü sonuçları, insider risk ilkesi önerisi ve önerilen ilkeyi oluşturmanıza hızlı bir şekilde yardımcı olmak için İlke oluştur düğmesini içerir. İlke oluştur'a seçerek ilke sihirbazına sizi otomatik olarak alır ve içgörüyle ilgili önerilen ilke şablonunu otomatik olarak seçer. Örneğin, çözümleme içgörü Veri sızıntı etkinliğine uygunsa, sizin  için ilke sihirbazında Genel veri sızıntıları ilkesi şablonu önceden seçilir.

![Insider risk yönetimi analizi ayrıntıları raporu.](../media/insider-risk-analytics-details.png)

### <a name="turn-off-analytics"></a>Analizi kapatma

Insider risk analizini kapatmak için *Insider Risk Yönetimi'ne*, *Insider Risk Yönetimi* Yöneticisi'ne veya Genel Microsoft 365 *rol grubuna üye* olmak gerekir. Analizi devre dışı bıraktıktan sonra, çözümleme içgörü raporları statik kalır ve yeni riskler için güncelleştirilmez.

Insider risk analizini kapatmak için aşağıdaki adımları tamamlayın:

1. Aşağıdaki [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne gidin**.
2. **Insider risk** **ayarlarıAnalytics** >  sayfası'ı seçin.
3. Analiz **sayfasında,** Olası **Insider risklerini tanımlamak için Kiracının kullanıcı etkinliğini tara'ya tıklayın'a tıklayın**.

## <a name="admin-notifications"></a>Yönetici bildirimleri

Yönetici bildirimleri, seçilebilir Insider risk yönetimi rol gruplarına otomatik olarak bir e-posta bildirimi gönderir. Aşağıdaki senaryolar için bildirimleri almak için bildirimleri etkinleştireblir ve hangi rol gruplarının bildirim atay postası ataysanız:

- Yeni bir ilke için ilk uyarı  oluşturularak bir bildirim e-postası gönderin. İlkeler, ilkeye yönelik sonraki uyarılarda ilk kez yapılan uyarılar ve bildirimler için her 24 saatte bir denetlenir.
- Yeni yüksek önem düzeyi uyarıları  oluşturularak günlük bir e-posta gönderin. İlkeler, yüksek önem derecesi uyarıları için her 24 saatte bir denetlenir.
- Çözümlenmemiş uyarılar içeren haftalık e-posta özetleme ilkeleri gönderme

Organizasyonunız için Insider risk yönetimi analizini etkinleştirdiyseniz, *Insider Risk Yönetimi* Yönetici rol grubu üyeleri, veri sızıntıları, hırsızlık ve sızıntı etkinlikleriyle ilgili ilk analiz öngörüleri için otomatik olarak bir e-posta bildirimi alırlar.

Yönetici ve analiz bildirimlerini devre dışı bırakmayı tercih ediyorsanız, aşağıdaki adımları tamamlayın:

1. Aşağıdaki [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimiInsider** >  **risk ayarları'ne gidin**.
2. Yönetici **bildirimleri sayfasını** seçin.
3. Aşağıdaki seçeneklerin uygun olduğu onay kutusunu temizleyin:
    - **Yeni bir ilke için ilk uyarı  oluşturularak bildirim e-postası gönderme**
    - **Analiz'de yeni bir içgörü olduğunda e-posta bildirimi gönderme**
    - **Analiz kapalıyken e-posta bildirimi gönderme**

4. Yapılandırmak **ve çıkmak** için Kaydet'i seçin.
