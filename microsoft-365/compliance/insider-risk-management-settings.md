---
title: Insider risk yönetimi ayarları
description: Microsoft Purview'da insider risk yönetimi ayarları hakkında bilgi edinin
keywords: Microsoft 365, Microsoft Purview, insider riski, risk yönetimi, uyumluluk
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
ms.openlocfilehash: 571f716a68bcbe9746338aec0fd9a6a3e8e9f0ef
ms.sourcegitcommit: b3f5fe84a319741583954ef8ff2ec9ec6da69bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2022
ms.locfileid: "65217630"
---
# <a name="get-started-with-insider-risk-management-settings"></a>Insider risk yönetimi ayarlarıyla Kullanmaya başlayın

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Insider risk yönetimi ayarları, ilke oluştururken seçtiğiniz şablondan bağımsız olarak tüm insider risk yönetimi ilkeleri için geçerlidir. Ayarlar, tüm **insider risk** yönetimi sayfalarının en üstünde bulunan Insider risk ayarları denetimi kullanılarak yapılandırılır. Bu ayarlar, aşağıdaki alanlar için ilke bileşenlerini denetler:

- [Gizlilik](#privacy)
- [Göstergeler](#indicators)
- [İlke zaman çerçeveleri](#policy-timeframes)
- [Akıllı algılamalar](#intelligent-detections)
- [Uyarıları dışarı aktarma](#export-alerts)
- [Öncelikli kullanıcı grupları (önizleme)](#priority-user-groups-preview)
- [Öncelikli fiziksel varlıklar (önizleme)](#priority-physical-assets-preview)
- [Power Automate akışları (önizleme)](#power-automate-flows-preview)
- [Microsoft Teams (önizleme)](#microsoft-teams-preview)
- [Analytics](#analytics)
- [Yönetici bildirimleri](#admin-notifications)

Başlamadan ve içeriden risk yönetimi ilkeleri oluşturmadan önce, bu ayarları anlamanız ve kuruluşunuz için uyumluluk gereksinimleri için en uygun ayar düzeylerini seçmeniz önemlidir.

## <a name="privacy"></a>Gizlilik

İlke eşleşmeleri olan kullanıcıların gizliliğini korumak önemlidir ve şirket içi risk uyarıları için veri araştırma ve analiz incelemelerinde nesnelliği artırmaya yardımcı olabilir. Insider risk ilkesi eşleşmesi olan kullanıcılar için aşağıdaki ayarlardan birini seçebilirsiniz:

- **Kullanıcı adlarının anonimleştirilmiş sürümlerini göster**: Yöneticilerin, veri araştırmacılarının ve gözden geçirenlerin ilke uyarılarıyla kimlerin ilişkili olduğunu görmesini önlemek için kullanıcı adları anonimleştirilir. Örneğin, 'Grace Taylor' kullanıcısı, insider risk yönetimi deneyiminin tüm alanlarında 'AnonIS8-988' gibi rastgele bir takma adla görünür. Bu ayarın seçilmesi, geçerli ve geçmiş ilke eşleşmeleri olan tüm kullanıcıları anonim hale getirir ve tüm ilkeler için geçerlidir. Insider risk uyarısında kullanıcı profili bilgileri ve servis talebi ayrıntıları bu seçenek seçildiğinde kullanılamaz. Ancak, mevcut ilkelere yeni kullanıcılar eklenirken veya yeni ilkelere kullanıcı atanırken kullanıcı adları görüntülenir. Bu ayarı kapatmayı seçerseniz, geçerli veya geçmiş ilke eşleşmeleri olan tüm kullanıcılar için kullanıcı adları görüntülenir.

    >[!IMPORTANT]
    >Microsoft 365 veya diğer sistemlerde şirket içinde risk uyarıları veya durumları olan kullanıcılar için bilgi tutarlılığını korumak için, dışarı aktarılan uyarılar için kullanıcı adlarının anonimleştirilmesi korunmaz. Dışarı aktarılan uyarılar, her uyarı için kullanıcı adlarını görüntüler.

- **Kullanıcı adlarının anonimleştirilmiş sürümlerini gösterme**: Uyarılar ve servis talepleri için geçerli ve geçmiş tüm ilke eşleşmeleri için kullanıcı adları görüntülenir. Kullanıcı profili bilgileri (ad, başlık, diğer ad ve kuruluş veya departman) tüm insider risk yönetimi uyarıları ve durumları için kullanıcı için görüntülenir.

![Insider risk yönetimi gizlilik ayarları.](../media/insider-risk-settings-privacy.png)

## <a name="indicators"></a>Göstergeler

Insider risk ilkesi şablonları, algılamak ve araştırmak istediğiniz risk etkinliklerinin türünü tanımlar. Her ilke şablonu, belirli tetikleyicilere ve risk etkinliklerine karşılık gelen belirli göstergeleri temel alır. Tüm göstergeler varsayılan olarak devre dışıdır ve insider risk yönetimi ilkesini yapılandırmadan önce bir veya daha fazla ilke göstergesi seçmeniz gerekir.

Uyarılar, kullanıcılar gerekli eşiği karşılayan ilke göstergeleriyle ilgili etkinlikler gerçekleştirdiğinde ilkeler tarafından tetiklenir. Insider risk yönetimi iki tür gösterge kullanır:

- **Olayları tetikleme**: Kullanıcının bir iç risk yönetimi ilkesinde etkin olup olmadığını belirleyen olaylar. Bir kullanıcı bir insider risk yönetimi ilkesine eklendiğinde tetikleyici bir olay yoksa, kullanıcı etkinliği ilke tarafından değerlendirilmez. Örneğin, Kullanıcı A, *veri hırsızlığından* oluşturulan bir ilkeye kullanıcı ilkesi şablonu ayrılarak eklenir ve ilke ve Microsoft 365 İk bağlayıcısı düzgün yapılandırılır. A Kullanıcısı İk bağlayıcısı tarafından bildirilen bir sonlandırma tarihine sahip olana kadar, Kullanıcı A etkinlikleri risk için bu iç risk yönetimi ilkesi tarafından değerlendirilmez. Tetikleme olayının bir diğer örneği, *veri sızıntısı* ilkelerini kullanırken kullanıcının *Yüksek* önem derecesi DLP ilkesi uyarısına sahip olmasıdır.
- **İlke göstergeleri**: Kapsam içi bir kullanıcının risk puanını belirlemek için kullanılan iç risk yönetimi ilkelerine dahil edilen göstergeler. Bu ilke göstergeleri yalnızca bir kullanıcı için tetikleme olayı gerçekleştikten sonra etkinleştirilir. İlke göstergelerine bazı örnekler, kullanıcının verileri kişisel bulut depolama hizmetlerine veya taşınabilir depolama cihazlarına kopyalaması, kullanıcı hesabının Azure Active Directory kaldırılması veya kullanıcının iç dosya ve klasörleri yetkisiz dış taraflarla paylaşmasıdır.

Belirli ilke göstergeleri, belirli ilke şablonları için tetikleyici olaylarını özelleştirmek için de kullanılabilir. İlke sihirbazında Öncelikli kullanıcı şablonlarına göre *Genel veri sızıntıları* veya *Veri sızıntıları* için yapılandırıldığında, bu göstergeler ilkeleriniz ve kullanıcılar ilke kapsamında olduğunda size daha fazla esneklik ve özelleştirme sağlar. Ayrıca, bir ilkede daha ayrıntılı denetim için bu tetikleyici göstergeleri için tek tek etkinlik eşikleri tanımlayabilirsiniz.

İlke göstergeleri aşağıdaki alanlara ayrılmıştır. İç risk ilkesi oluştururken gösterge olay sınırlarını her gösterge düzeyi için etkinleştirmek ve özelleştirmek için göstergeleri seçebilirsiniz:

- **Office göstergeleri**: Bunlar SharePoint siteleri, Microsoft Teams ve e-posta iletileri için ilke göstergelerini içerir.
- **Cihaz göstergeleri**: Bunlar, ağ üzerinden veya cihazlarla dosya paylaşma gibi etkinliklere yönelik ilke göstergelerini içerir. Göstergeler, yürütülebilir (.exe) ve dinamik bağlantı kitaplığı (.dll) dosya etkinliği hariç olmak üzere tüm dosya türlerini içeren etkinlikleri içerir. *Cihaz göstergeleri'ni* seçerseniz, Windows 10 Derleme 1809 veya üzeri ve macOS (Catalina 10.15 veya üzeri) cihazlar için etkinlik işlenir. Hem Windows hem de macOS cihazları için öncelikle cihazları uyumluluk portalına eklemeniz gerekir. Cihaz göstergeleri ayrıca kuruluşunuzun Microsoft Edge ve Google Chrome'da görüntülenen, kopyalanan, paylaşılan veya yazdırılan yürütülemeyen dosyalar için sızdırma sinyallerini algılamasına ve bu sinyaller üzerinde işlem gerçekleştirmesine yardımcı olan tarayıcı sinyal algılamasını içerir. Windows cihazları insider riskiyle tümleştirme için yapılandırma hakkında daha fazla bilgi için bu makalenin Cihaz [göstergelerini ve ekleme Windows cihazlarını etkinleştirme](insider-risk-management-settings.md#OnboardDevices) bölümüne bakın. macOS cihazlarını insider riskiyle tümleştirme için yapılandırma hakkında daha fazla bilgi için, bu makalenin Aşağıdaki Cihaz göstergelerini ve macOS cihazlarını ekleme özelliğini etkinleştirme bölümüne bakın. Tarayıcı sinyali algılama hakkında daha fazla bilgi için bkz. [Insider risk yönetimi tarayıcısı sinyal algılama hakkında bilgi edinin ve yapılandırın](insider-risk-management-browser-support.md).
- **Güvenlik ilkesi ihlal göstergesi (önizleme)**: Bunlar onaylanmamış veya kötü amaçlı yazılım yükleme veya güvenlik denetimlerini atlamayla ilgili Uç Nokta için Microsoft Defender göstergelerini içerir. Insider risk yönetiminde uyarı almak için etkin bir Uç Nokta için Defender lisansına ve insider risk tümleştirmesine sahip olmanız gerekir. İç risk yönetimi tümleştirmesi için Uç Nokta için Defender'ı yapılandırma hakkında daha fazla bilgi için bkz[. Uç Nokta için Microsoft Defender'de gelişmiş özellikleri yapılandırma](/windows/security/threat-protection/microsoft-defender-atp/advanced-features\#share-endpoint-alerts-with-microsoft-compliance-center).
- **Sağlık kaydı erişim göstergeleri (önizleme):** Bunlar hasta tıbbi kaydı erişimi için ilke göstergelerini içerir. Örneğin, elektronik tıbbi kayıtlarınızdaki (EMR) sistem günlüklerinizdeki hasta tıbbi kayıtlarına erişim girişimi, insider risk yönetimi sağlık ilkeleriyle paylaşılabilir. Insider risk yönetiminde bu tür uyarıları almak için, sağlık hizmetleriyle ilgili bir veri bağlayıcısı ve İk veri bağlayıcısının yapılandırılmış olması gerekir.
- **Fiziksel erişim göstergeleri (önizleme):** Bunlar hassas varlıklara fiziksel erişim için ilke göstergelerini içerir. Örneğin, fiziksel bağlantı sistemi günlüklerinizdeki kısıtlı bir alana erişim girişimi, içeriden risk yönetimi ilkeleriyle paylaşılabilir. Insider risk yönetiminde bu tür uyarıları almak için, insider risk yönetiminde etkinleştirilmiş öncelikli fiziksel varlıklara ve yapılandırılmış [Fiziksel badging veri bağlayıcısına](import-physical-badging-data.md) sahip olmanız gerekir. Fiziksel erişimi yapılandırma hakkında daha fazla bilgi edinmek için bu makaledeki [Öncelik fiziksel erişimi bölümüne bakın](#priority-physical-assets-preview) .
- **Microsoft Defender for Cloud Apps göstergeleri (önizleme):** Bunlar, Bulut için Defender Uygulamalarından paylaşılan uyarılardan ilke göstergelerini içerir. Bulut için Defender Uygulamaları'nda otomatik olarak etkinleştirilen anomali algılama, sonuçları hemen algılamaya ve harmanlama işlemine başlar ve kullanıcılarınız ile ağınıza bağlı makineler ve cihazlar genelinde çok sayıda davranışsal anomaliyi hedefler. Bu etkinlikleri insider risk yönetimi ilkesi uyarılarına eklemek için bu bölümdeki bir veya daha fazla göstergeyi seçin. Bulut için Defender Apps analizi ve anomali algılama hakkında daha fazla bilgi edinmek için bkz. [Davranış analizi ve anomali algılamayı alma](/cloud-app-security/anomaly-detection-policy).
- **Risk puanı artırıcıları**: Bunlar, bir gün boyunca veya ilke ihlali olarak çözümlenmiş önceki durumları olan kullanıcılar için kullanıcının olağan etkinliğinin üzerinde olan etkinlik için risk puanını yükseltmeyi içerir. Risk puanı artırıcıların etkinleştirilmesi, risk puanlarını ve bu tür etkinlikler için uyarı olasılığını artırır. Bir gün boyunca kullanıcının olağan etkinliğinin üzerinde olan etkinlik için, algılanan etkinlik kullanıcının tipik davranışından saparsa puanlar artırılır. İlke ihlali olarak çözümlenmiş önceki durumları olan kullanıcılar için, bir kullanıcının daha önce onaylanmış bir ilke ihlali olarak çözümlenmiş birden fazla olayı varsa puanlar artırılır. Risk puanı güçlendiricileri yalnızca bir veya daha fazla gösterge seçiliyse seçilebilir.

Bazı durumlarda, kuruluşunuzdaki insider risk ilkelerine uygulanan insider risk ilkesi göstergelerini sınırlamak isteyebilirsiniz. Belirli alanlar için ilke göstergelerini tüm insider risk ilkelerinden devre dışı bırakarak kapatabilirsiniz. Olayları tetikleme yalnızca Öncelikli kullanıcı şablonları tarafından *Genel veri sızıntıları* veya *Veri sızıntılarından oluşturulan ilkeler* için değiştirilebilir. Diğer tüm şablonlardan oluşturulan ilkelerin özelleştirilebilir tetikleyici göstergeleri veya olayları yoktur.

Tüm insider risk ilkelerinde etkinleştirilen insider risk ilkesi göstergelerini tanımlamak için **Insider risk** **ayarlarıIndicators'a** >  gidin ve bir veya daha fazla ilke göstergesi seçin. Göstergeler ayarları sayfasında seçilen göstergeler, ilke sihirbazında insider risk ilkesi oluşturulurken veya düzenlenirken tek tek yapılandırılamaz.

> [!NOTE]
> El ile eklenen yeni kullanıcıların **Kullanıcılar panosunda** görünmesi birkaç saat sürebilir. Bu kullanıcılar için önceki 90 güne ilişkin etkinliklerin görüntülenmesi 24 saat kadar sürebilir. El ile eklenen kullanıcıların etkinliklerini görüntülemek için **Kullanıcılar panosunda** kullanıcıyı seçin ve ayrıntılar bölmesindeki **Kullanıcı etkinliği** sekmesini açın.

### <a name="enable-device-indicators-and-onboard-windows-devices"></a>Cihaz göstergelerini etkinleştirme ve Windows cihazları ekleme
<a name="OnboardDevices"> </a>

Windows cihazlarda risk etkinliklerinin izlenmesini etkinleştirmek ve bu etkinlikler için ilke göstergeleri eklemek için Windows cihazlarınız aşağıdaki gereksinimleri karşılamalı ve aşağıdaki ekleme adımlarını tamamlamanız gerekir.

#### <a name="step-1-prepare-your-endpoints"></a>1. Adım: Uç noktalarınızı hazırlama

Şirket içi risk yönetiminde raporlamayı planladığınız Windows 10 cihazlarının bu gereksinimleri karşıladığından emin olun.

1. x64 derlemesi 1809 veya sonraki Windows 10 çalıştırıyor olması ve 20 Şubat [2020'den itibaren Windows 10 güncelleştirmesini (İs Derlemesi 17763.1075)](https://support.microsoft.com/help/4537818/windows-10-update-kb4537818) yüklemiş olması gerekir.
2. Windows 10 cihazında oturum açmak için kullanılan kullanıcı hesabı etkin bir Azure Active Directory (AAD) hesabı olmalıdır. Windows 10 cihaz [AAD](/azure/active-directory/devices/concept-azure-ad-join), karma AAD veya Active Directory'ye katılmış ya da AAD kayıtlı olabilir.
3. Bulut karşıya yükleme etkinliğinin eylemlerini izlemek için uç nokta cihazına Microsoft Edge tarayıcısını yükleyin. Bkz. [Chromium temelinde yeni Microsoft Edge indirme](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium).

#### <a name="step-2-onboarding-devices"></a>2. Adım: Cihazları ekleme
<a name="OnboardStep2"> </a>

Bir cihazda insider risk yönetimi etkinliklerini izleyebilmeniz için önce cihaz izlemeyi etkinleştirmeniz ve uç noktalarınızı eklemeniz gerekir. Her iki eylem de Microsoft Purview uyumluluk portalında gerçekleştirilen işlemlerdir.

Henüz eklenmemiş cihazları eklemek istediğinizde, aşağıdaki adımlarda açıklandığı gibi uygun betiği indirecek ve dağıtacaksınız.

[Uç Nokta için Microsoft Defender'a](/windows/security/threat-protection/) eklenen cihazlarınız zaten yönetilen cihazlar listesinde görünür. [Sonraki bölümde Uç Nokta için Microsoft Defender eklenen cihazlarınız varsa 3. Adımı](insider-risk-management-settings.md#OnboardStep3) izleyin.

Bu dağıtım senaryosunda, henüz eklenmemiş cihazları eklersiniz ve yalnızca Windows 10 cihazlarda insider risk etkinliklerini izlemek istersiniz.

1. [Microsoft Purview uyumluluk portalını](https://compliance.microsoft.com) açın.
2. Uyumluluk portalı ayarları sayfasını açın ve **Cihazları ekleme'yi** seçin.

   > [!NOTE]
   > Cihaz eklemenin etkinleştirilmesi genellikle yaklaşık 60 saniye sürer ancak lütfen Microsoft desteğiyle etkileşime geçmeden önce 30 dakikaya kadar bekleyin.

3. **Cihazlar** listesini açmak için **Cihaz yönetimi'ni** seçin. Siz cihazları ekleyene kadar liste boş kalır.
4. **Ekleme** işlemini başlatmak için Ekleme'yi seçin.
5. **Dağıtım yöntemi** listesinden bu daha fazla cihaza dağıtmak istediğiniz yöntemi seçin ve ardından **paketi indirin**.
6. [Windows 10 makineleri için ekleme araçları ve yöntemlerinde uygun yordamları](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints) izleyin. Bu bağlantı sizi 5. adımda seçtiğiniz dağıtım paketiyle eşleşen Uç Nokta için Microsoft Defender yordamlara erişebileceğiniz bir giriş sayfasına götürür:
    - grup ilkesi kullanarak Windows 10 makineleri ekleme
    - Microsoft Endpoint Configuration Manager kullanarak Windows makineleri ekleme
    - Mobil Cihaz Yönetimi araçlarını kullanarak Windows 10 makineleri ekleme
    - Yerel betik kullanarak Windows 10 makineleri ekleme
    - Kalıcı olmayan sanal masaüstü altyapısı (VDI) makineleri ekleme.

İşlem tamamlandıktan ve uç nokta eklendikten sonra cihaz listesinde görünür olmalıdır ve uç nokta denetim etkinlik günlüklerini insider risk yönetimine raporlamaya başlar.

> [!NOTE]
> Bu deneyim, lisans zorlaması altındadır. Gerekli lisans olmadan veriler görünür veya erişilebilir olmaz.

#### <a name="step-3-if-you-have-devices-onboarded-into-microsoft-defender-for-endpoint"></a>3. Adım: Uç Nokta için Microsoft Defender'a eklenen cihazlarınız varsa
<a name="OnboardStep3"> </a>

Uç Nokta için Microsoft Defender zaten dağıtılmışsa ve içinde raporlama yapılan uç noktalar varsa, tüm bu uç noktalar yönetilen cihazlar listesinde görünür. [2. Adım: Cihazları](insider-risk-management-settings.md#OnboardStep2) ekleme bölümünü kullanarak kapsamı genişletmek için yeni cihazları insider risk yönetimine eklemeye devam edebilirsiniz.

1. [Microsoft Purview uyumluluk portalını](https://compliance.microsoft.com) açın.
2. Uyumluluk portalı ayarları sayfasını açın ve **Cihaz izlemeyi etkinleştir'i** seçin.
3. **Cihazlar** listesini açmak için **Cihaz yönetimi'ni** seçin. Zaten Uç Nokta için Microsoft Defender raporlaması yapılan cihazların listesini görmeniz gerekir.
4. Daha fazla cihaz **eklemeniz** gerekiyorsa Ekleme'yi seçin.
5. **Dağıtım yöntemi** listesinden bu daha fazla cihaza dağıtmak istediğiniz yöntemi seçin ve ardından **Paketi indir'i** seçin.
6. [Windows 10 makineleri için ekleme araçları ve yöntemlerinde uygun yordamları](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints) izleyin. Bu bağlantı sizi 5. adımda seçtiğiniz dağıtım paketiyle eşleşen Uç Nokta için Microsoft Defender yordamlara erişebileceğiniz bir giriş sayfasına götürür:
    - grup ilkesi kullanarak Windows 10 makineleri ekleme
    - Microsoft Endpoint Configuration Manager kullanarak Windows makineleri ekleme
    - Mobil Cihaz Yönetimi araçlarını kullanarak Windows 10 makineleri ekleme
    - Yerel betik kullanarak Windows 10 makineleri ekleme
    - Kalıcı olmayan sanal masaüstü altyapısı (VDI) makineleri ekleme.

İşlem tamamlandıktan ve uç nokta eklendikten sonra **Cihazlar** tablosunun altında görünür olmalıdır ve uç nokta denetim etkinliği günlüklerini insider risk yönetimine raporlamaya başlar.

> [!NOTE]
>Bu deneyim, lisans zorlaması altındadır. Gerekli lisans olmadan veriler görünür veya erişilebilir olmaz.

### <a name="enable-device-indicators-and-onboard-macos-devices"></a>Cihaz göstergelerini etkinleştirme ve macOS cihazlarını ekleme

macOS cihazları (Catalina 10.15 veya üzeri), Intune veya JAMF Pro kullanılarak insider risk yönetimi ilkelerini desteklemek için Microsoft 365 eklenebilir. Daha fazla bilgi ve yapılandırma kılavuzu için bkz. [macOS cihazlarını Microsoft 365 genel bakışa ekleme (önizleme)](device-onboarding-macos-overview.md).

### <a name="indicator-level-settings-preview"></a>Gösterge düzeyi ayarları (önizleme)

İlke sihirbazında bir ilke oluştururken, günlük risk olay sayısının içeriden risk uyarıları için risk puanını nasıl etkileyebileceğini yapılandırabilirsiniz. Bu gösterge ayarları, kuruluşunuzdaki risk olaylarının oluşum sayısının risk puanını ve dolayısıyla bu olaylar için ilişkili uyarı önem derecesini nasıl etkileyeceğini denetlemenize yardımcı olur. İsterseniz, tüm etkin göstergeler için Microsoft tarafından önerilen varsayılan olay eşiği düzeylerini korumayı da seçebilirsiniz.

Örneğin, iç risk ilkesi ayarlarında SharePoint göstergeleri etkinleştirmeye ve yeni bir iç risk *Veri sızıntısı* ilkesi için göstergeleri yapılandırırken SharePoint olaylar için **özel eşikler ayarlamaya** karar verirsiniz. Insider risk ilkesi sihirbazındayken, bu olaylarla ilişkili uyarıların risk puanını etkilemek için her SharePoint göstergesi için üç farklı günlük olay düzeyi yapılandırabilirsiniz.

![Insider risk yönetimi özel gösterge ayarları.](../media/insider-risk-custom-indicators.png)

İlk günlük olay düzeyi için eşiği, olaylar için risk puanına daha düşük bir etki için *günde 10 veya daha fazla olay* , olaylar için risk puanına orta etki için *günde 20 veya daha fazla olay* ve olaylar için risk puanına *günde 30 veya daha fazla olay* daha yüksek bir etki olacak şekilde ayarlarsınız. Bu ayarlar etkili bir şekilde şu anlama gelir:

- Olay tetiklendikten sonra gerçekleşen 1-9 SharePoint olay varsa risk puanları minimum düzeyde etkilenir ve uyarı oluşturmama eğilimi gösterir.
- Tetikleme olayından sonra gerçekleşen 10-19 SharePoint olay varsa risk puanı doğal olarak daha düşüktür ve uyarı önem derecesi düzeyleri düşük düzeyde olabilir.
- Tetikleme sonrasında gerçekleşen 20-29 SharePoint olay varsa, risk puanı doğal olarak daha yüksektir ve uyarı önem düzeyleri orta düzeyde olma eğilimindedir.
- Tetiklemeden sonra gerçekleşen 30 veya daha fazla SharePoint olay varsa, risk puanı doğal olarak daha yüksektir ve uyarı önem düzeyleri yüksek düzeyde olabilir.

İlke eşikleri için bir diğer seçenek, ilkeyi tetikleyen olayı kullanıcılar için normal günlük etkinlik miktarının üzerinde olan etkinliğe atamaktır. Her eşik, belirli eşik ayarlarıyla tanımlanmak yerine kapsam içi ilke kullanıcıları için algılanan anormal etkinlikler için dinamik olarak özelleştirilir. Anormal etkinlikler için eşik etkinliği tek bir gösterge için destekleniyorsa, bu göstergenin ilke sihirbazında **Etkinlik kullanıcının günlük olağan etkinliğinin üzerindedir'i** seçebilirsiniz. Bu seçenek listelenmiyorsa, göstergede anormal etkinlik tetikleme özelliği kullanılamaz. **Etkinlik kullanıcının gün için olağan etkinliğinin üzerindeyse** seçeneği bir gösterge için listeleniyor ancak seçilemiyorsa, **Insider risk ayarlarıİlke** >  **göstergelerinde** bu seçeneği etkinleştirmeniz gerekir.

## <a name="policy-timeframes"></a>İlke zaman çerçeveleri

İlke zaman çerçeveleri, insider risk yönetimi ilke şablonları için olaylara ve etkinliklere göre ilke eşleşmelerinden sonra tetiklenen geçmiş ve gelecekteki gözden geçirme dönemlerini tanımlamanızı sağlar. Seçtiğiniz ilke şablonuna bağlı olarak, aşağıdaki ilke zaman çerçeveleri kullanılabilir:

- **Etkinleştirme penceresi**: Tüm ilke şablonları için kullanılabilir olan *Etkinleştirme penceresi* , bir tetikleme olayından **sonra** pencerenin etkinleştirilmesi için tanımlanan gün sayısıdır. Pencere, ilkeye atanan herhangi bir kullanıcı için tetikleme olayı gerçekleştikten sonra 1 ile 30 gün boyunca etkinleştirilir. Örneğin, bir insider risk yönetimi ilkesi yapılandırıp *Etkinleştirme penceresini* 30 gün olarak ayarladınız. İlkeyi yapılandırdığınızdan bu yana birkaç ay geçti ve ilkeye dahil edilen kullanıcılardan biri için bir tetikleyici olay gerçekleşir. Tetikleme olayı *Etkinleştirme penceresini* etkinleştirir ve bu kullanıcı için ilke, tetikleme olayı gerçekleştikten sonra 30 gün boyunca etkindir.
- **Geçmiş etkinlik algılama**: Tüm ilke şablonları için kullanılabilir olan *Geçmiş etkinlik algılama* , pencerenin tetikleme olayından **önce** etkinleştirilmesi gereken tanımlı gün sayısıdır. Pencere, ilkeye atanan herhangi bir kullanıcı için tetikleme olayı gerçekleşmeden önce 0 ile 90 gün boyunca etkinleştirilir. Örneğin, bir insider risk yönetimi ilkesi yapılandırıp *Geçmiş etkinlik algılamayı* 90 gün olarak ayarladınız. İlkeyi yapılandırdığınızdan bu yana birkaç ay geçti ve ilkeye dahil edilen kullanıcılardan biri için bir tetikleyici olay gerçekleşir. Tetikleme olayı *Geçmiş etkinlik algılamasını* etkinleştirir ve ilke, tetikleme olayından önceki 90 gün boyunca bu kullanıcı için geçmiş etkinlikleri toplar.

![Insider risk yönetimi zaman çerçevesi ayarları.](../media/insider-risk-settings-timeframes.png)

## <a name="intelligent-detections"></a>Akıllı algılamalar

Akıllı algılama ayarları, riskli etkinliklerin algılamalarının uyarılar için nasıl işlendiğini iyileştirmeye yardımcı olur. Bazı durumlarda, yoksaymak için dosya türleri tanımlamanız gerekebilir veya kullanıcılar için risk puanlarını artırmak için günlük olaylar için bir algılama düzeyi uygulamak isteyebilirsiniz. Dosya türü dışlamalarını denetlemek, olağan dışı etkinlikler için risk puanını artırmak ve dosya hacmi sınırlarını artırmak için bu ayarları kullanın.

### <a name="file-type-exclusions"></a>Dosya türü dışlamaları

Belirli dosya türlerini tüm insider risk yönetimi ilkesi eşleştirmelerinin dışında tutmak için dosya türü uzantılarını virgülle ayırarak girin. Örneğin, belirli türlerdeki müzik dosyalarını ilke eşleşmelerinin dışında tutmak için **Dosya türü dışlamaları** alanına *aac,mp3,wav,wma* girebilirsiniz. Bu uzantılara sahip dosyalar tüm insider risk yönetimi ilkeleri tarafından yoksayılır.

### <a name="minimum-number-of-daily-events-to-boost-score-for-unusual-activity"></a>Olağan dışı etkinlikler için puanı artırmak için en az günlük etkinlik sayısı

Bu ayarla, bir kullanıcı için olağan dışı olarak kabul edilen etkinliğin risk puanını artırmak için kaç günlük olayın gerekli olduğunu tanımlarsınız. Örneğin, bu risk güçlendirici için 25 girdiğinizi varsayalım. Bir kullanıcı son 30 gün içinde ortalama 10 dosya indirmesi gerçekleştiriyorsa ancak ilke bir günde 20 dosya indirdiğini algılarsa, o gün indirdiği dosya sayısı bu risk artırıcı için girdiğiniz sayıdan daha az olduğundan bu kullanıcı için olağan dışı olsa bile bu etkinliğin puanı yükseltilmeyecektir.

### <a name="alert-volume"></a>Uyarı birimi

Insider risk ilkeleri tarafından algılanan kullanıcı etkinliklerine, uyarı önem derecesini (düşük, orta, yüksek) belirleyen belirli bir risk puanı atanır. Varsayılan olarak, belirli miktarda düşük, orta ve yüksek önem derecesi uyarısı oluştururuz, ancak sesi gereksinimlerinize uyacak şekilde artırabilir veya azaltabilirsiniz. Tüm insider risk yönetimi ilkeleri için uyarı hacmini ayarlamak için aşağıdaki ayarlardan birini seçin:

- **Daha az uyarı**: Tüm yüksek önem dereceli uyarıları, daha az orta önem derecesi uyarılarını ve düşük önem derecesini görürsünüz. Bu ayar düzeyi, bazı gerçek pozitif değerleri kaçırabileceğiniz anlamına gelir.
- **Varsayılan birim**: Tüm yüksek önem dereceli uyarıları ve dengeli miktarda orta ve düşük önem derecesi uyarılarını görürsünüz.
- **Daha fazla uyarı**: Tüm orta ve yüksek önem dereceli uyarıları ve en düşük önem derecesi uyarılarını görürsünüz. Bu ayar düzeyi daha fazla hatalı pozitif sonuç verebilir.

### <a name="microsoft-defender-for-endpoint-preview"></a>Uç Nokta için Microsoft Defender (önizleme)

[Uç Nokta için Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection), kurumsal ağların gelişmiş tehditleri engellemesine, algılamasına, araştırmasına ve yanıtlamasına yardımcı olmak için tasarlanmış bir kurumsal uç nokta güvenlik platformudur. Kuruluşunuzdaki güvenlik ihlallerini daha iyi görmek için, insider risk yönetimi güvenlik ihlali ilke şablonlarından oluşturulan ilkelerde kullanılan etkinlikler için Uç Nokta için Defender uyarılarını içeri aktarabilir ve filtreleyebilirsiniz.

İlgilendiğiniz sinyal türlerine bağlı olarak, Uç Nokta için Defender uyarı önceliklendirme durumuna göre uyarıları insider risk yönetimine aktarmayı seçebilirsiniz. İçeri aktarabileceğiniz genel ayarlarda aşağıdaki uyarı önceliklendirme durumlarından birini veya daha fazlasını tanımlayabilirsiniz:

- Unknown
- Yeni
- Devam ediyor
- Çözülmüş

Uç Nokta için Defender'dan gelen uyarılar günlük olarak içeri aktarılır. Seçtiğiniz önceliklendirme durumuna bağlı olarak, Uç Nokta için Defender'da önceliklendirme durumu değiştikçe aynı uyarı için birden çok kullanıcı etkinliği görebilirsiniz.

Örneğin, bu ayar için *Yeni*, *Devam Ediyor* ve *Çözümlendi'yi* seçerseniz, bir Uç Nokta için Microsoft Defender uyarısı oluşturulduğunda ve durum *Yeni* olduğunda, iç risk altındaki kullanıcı için bir ilk uyarı etkinliği içeri aktarılır. Uç Nokta için Defender önceliklendirme durumu *Sürüyor olarak değiştiğinde*, bu uyarı için ikinci bir etkinlik, içeriden risk altındaki kullanıcı için içeri aktarılır. Son Uç Nokta için Defender önceliklendirme durumu *Çözüldü* olarak ayarlandığında, iç risk altındaki kullanıcı için bu uyarı için üçüncü bir etkinlik içeri aktarılır. Bu işlev, araştırmacıların Uç Nokta için Defender uyarılarının ilerleme durumunu izlemesine ve araştırmalarının gerektirdiği görünürlük düzeyini seçmesine olanak tanır.

> [!IMPORTANT]
> Güvenlik ihlali uyarılarını içeri aktarmak için kuruluşunuzda Uç Nokta için Microsoft Defender yapılandırmanız ve Defender Güvenlik Merkezi'nde insider risk yönetimi tümleştirmesi için Uç Nokta için Defender'ı etkinleştirmeniz gerekir. Şirket içi risk yönetimi tümleştirmesi için Uç Nokta için Defender'ı yapılandırma hakkında daha fazla bilgi için bkz. [Uç Nokta için Defender'da gelişmiş özellikleri yapılandırma](/windows/security/threat-protection/microsoft-defender-atp/advanced-features\#share-endpoint-alerts-with-microsoft-compliance-center).

### <a name="domains"></a>Etki alanları

Etki alanı ayarları, belirli etki alanlarına yönelik etkinlikler için risk düzeylerini tanımlamanıza yardımcı olur. Bu etkinlikler arasında dosya paylaşımı, e-posta iletileri gönderme, içerik indirme veya karşıya yükleme yer alır. Bu ayarlarda etki alanları belirterek, bu etki alanlarıyla gerçekleşen etkinlik için risk puanlama oranını artırabilir veya azaltabilirsiniz.

Etki alanı ayarlarının her biri için bir etki alanı tanımlamak için Etki alanı ekle'yi kullanın. Ayrıca, kök etki alanlarının veya alt etki alanlarının varyasyonlarını eşleştirmeye yardımcı olması için joker karakterler kullanabilirsiniz. Örneğin, sales.wingtiptoys.com ve support.wingtiptoys.com belirtmek için, bu alt etki alanlarıyla (ve aynı düzeydeki diğer alt etki alanlarıyla) eşleştirmek için '*.wingtiptoys.com' joker girdisini kullanırsınız. Kök etki alanı için çok düzeyli alt etki alanları belirtmek için Çok **Düzeyli Alt** Etki Alanları Ekle onay kutusunu seçmeniz gerekir.

Aşağıdaki etki alanı ayarlarının her biri için en fazla 500 etki alanı girebilirsiniz:

- **İzin verilmeyen etki alanları:** İzin verilmeyen etki alanları belirtildiğinde, bu etki alanlarıyla gerçekleştirilir etkinliğin risk puanları *daha yüksek* olur. Bazı örnekler, bir kişiyle içerik paylaşma (gmail.com adresi olan birine e-posta gönderme gibi) ve kullanıcılar bu izin verilmeyen etki alanlarından birinden cihaza içerik indirdiğinde gerçekleştirilir.
- **İzin verilen etki alanları:** İzin verilen etki alanlarıyla ilgili bazı etkinlikler ilkeleriniz tarafından yoksayılır ve uyarı oluşturmaz. Bu etkinlikler şunlardır:

    - Dış etki alanlarına gönderilen e-posta
    - Dış etki alanlarıyla paylaşılan dosyalar, klasörler, siteler
    - Dış etki alanlarına yüklenen dosyalar (Microsoft Edge tarayıcı kullanılarak)

    Ayarlarda izin verilen etki alanları belirtildiğinde, bu etki alanlarıyla yapılan bu etkinlik, iç kuruluş etkinliğinin nasıl ele alındıklarına benzer şekilde değerlendirilir. Örneğin, buraya etkinliklerle eşlenen etki alanları, kuruluşunuzun dışındaki biriyle (gmail.com adresi olan birine e-posta göndermek gibi) içerik paylaşmayı içerebilir.

- **Üçüncü taraf etki alanları:** Kuruluşunuz iş amacıyla (bulut depolama gibi) üçüncü taraf etki alanları kullanıyorsa, cihaz göstergesiyle ilgili etkinlik uyarıları alabilmeniz için bunları buraya ekleyin. *Üçüncü taraf bir siteden içerik indirmek için tarayıcı kullanın*.

## <a name="export-alerts"></a>Uyarıları dışarı aktarma

Insider risk yönetimi uyarı bilgileri, [Office 365 Yönetim Etkinliği API'si şeması](/office/office-365-management-api/office-365-management-activity-api-schema#security-and-compliance-alerts-schema) kullanılarak güvenlik bilgilerine ve olay yönetimine (SIEM) ve güvenlik düzenleme otomatik yanıtı (SOAR) çözümlerine aktarılabilir. Uyarı bilgilerini kuruluşunuzun insider risk bilgilerini yönetmek veya toplamak için kullanabileceği diğer uygulamalara aktarmak için Office 365 Yönetim Etkinliği API'lerini kullanabilirsiniz. Uyarı bilgileri, Office 365 Yönetim Etkinliği API'leri aracılığıyla her 60 dakikada bir dışarı aktarılır ve kullanılabilir.

Kuruluşunuz Microsoft Sentinel kullanıyorsa, insider risk uyarısı bilgilerini Sentinel'e aktarmak için kullanıma açık insider risk yönetimi veri bağlayıcısını da kullanabilirsiniz. Daha fazla bilgi için Microsoft Sentinel makalesindeki [Insider Risk Management (IRM) (Önizleme)](/azure/sentinel/data-connectors-reference#microsoft-365-insider-risk-management-irm-preview) bölümüne bakın.

>[!IMPORTANT]
>Microsoft 365 veya diğer sistemlerde şirket içinde risk uyarıları veya durumları olan kullanıcılar için bilgi tutarlılığını korumak için, dışarı aktarılan uyarılar için kullanıcı adlarının anonimleştirilmesi korunmaz. Dışarı aktarılan uyarılar, her uyarı için kullanıcı adlarını görüntüler.

INSIDER risk uyarısı bilgilerini gözden geçirmek için API'leri kullanmak için:

1. **Insider risk yönetimi** >  **Ayarlar** >  **Export uyarılarında** Office 365 Yönetim Etkinliği API'si desteğini etkinleştirin. Varsayılan olarak, bu ayar Microsoft 365 kuruluşunuz için devre dışı bırakılır.
2. *SecurityComplianceAlerts* tarafından yaygın Office 365 denetim etkinliklerini filtreleyin.
3. *SecurityComplianceAlerts* öğesini *InsiderRiskManagement* kategorisine göre filtreleyin.

![Insider risk yönetimi dışarı aktarma uyarı ayarları.](../media/insider-risk-settings-export.png)

Uyarı bilgileri, güvenlik ve uyumluluk uyarı şemasından ve Office 365 Yönetim Etkinliği API'sinin ortak şemasından gelen bilgileri içerir.

Aşağıdaki alanlar ve değerler, Güvenlik & Uyumluluğu uyarı şeması için insider risk yönetimi uyarıları için dışarı aktarılır:

| **Uyarı parametresi** | **Açıklama** |
|:------------------|:----------------|
| Alerttype | Uyarının türü *Özel'dir*.  |
| AlertId | Uyarının GUID'i. Insider risk yönetimi uyarıları değişebilir. Uyarı durumu değiştikçe, aynı AlertID'ye sahip yeni bir günlük oluşturulur. Bu AlertID, bir uyarının güncelleştirmelerini ilişkilendirmek için kullanılabilir. |
| Kategori | Uyarının kategorisi *InsiderRiskManagement'tır*. Bu kategori, bu uyarıları diğer Güvenlik & Uyumluluk uyarılarından ayırmak için kullanılabilir. |
| Açıklamalar | Uyarı için varsayılan açıklamalar. Değerler *Yeni Uyarıdır* (bir uyarı oluşturulduğunda günlüğe kaydedilir) ve *Uyarı Güncelleştirildi* (bir uyarı güncelleştirmesi olduğunda günlüğe kaydedilir). Uyarı güncelleştirmelerini ilişkilendirmek için AlertID kullanın. |
| Veri | Uyarının verileri benzersiz kullanıcı kimliğini, kullanıcı asıl adını ve kullanıcının bir ilkede tetiklendiğinde tarih ve saati (UTC) içerir. |
| Name | Uyarıyı oluşturan insider risk yönetimi ilkesinin ilke adı. |
| policyid | Uyarıyı tetikleyen insider risk yönetimi ilkesinin GUID'i. |
| Önem | Uyarının önem derecesi. Değerler *Yüksek*, *Orta* veya *Düşük'tir*. |
| Kaynak | Uyarının kaynağı. Değer *Office 365 Güvenlik & Uyumluluğu'dur*. |
| Durum | Uyarının durumu. Değerler *Etkin* (insider riskinde *gözden geçirme gerekiyor* ), *Araştırma* (insider riskinde *onaylandı* ), *Çözüldü* (insider riskinde *çözümlendi* ), *Kapatıldı* (insider riskinde *kapatıldı* ). |
| Sürüm | Güvenlik ve uyumluluk uyarı şemasının sürümü. |

Aşağıdaki alanlar ve değerler[, Office 365 Yönetim Etkinliği API'sinin ortak şeması](/office/office-365-management-api/office-365-management-activity-api-schema#common-schema) için insider risk yönetimi uyarıları için dışarı aktarılır.

- Userıd
- Kimliği
- Kayıt Türü
- CreationTime
- Işlem
- OrganizationId
- Usertype
- UserKey

## <a name="priority-user-groups-preview"></a>Öncelikli kullanıcı grupları (önizleme)

Kuruluşunuzdaki kullanıcılar konumlarına, hassas bilgilere erişim düzeylerine veya risk geçmişine bağlı olarak farklı risk düzeylerine sahip olabilir. Bu kullanıcıların etkinliklerinin incelenmesine ve puanlanmasına öncelik vermek, kuruluşunuz için daha yüksek sonuçlar doğurabilecek olası riskler konusunda sizi uyarmaya yardımcı olabilir. Insider risk yönetimindeki öncelikli kullanıcı grupları, kuruluşunuzda daha yakın inceleme ve daha hassas risk puanlaması gerektiren kullanıcıları tanımlamaya yardımcı olur. *Öncelikli kullanıcılara göre Güvenlik ilkesi ihlalleri* ve öncelikli kullanıcılar ilke şablonları *tarafından veri sızıntıları* ile birleştiğinde, öncelikli bir kullanıcı grubuna eklenen kullanıcıların şirket içi risk uyarıları ve daha yüksek önem düzeyine sahip uyarılar olasılığı artar.

![Insider risk yönetimi öncelikli kullanıcı grubu ayarları.](../media/insider-risk-settings-priority-users.png)

Öncelik kullanıcı gruplarının tüm analistler ve araştırmacılar tarafından gözden geçirilmeye açık olması yerine, gözden geçirme etkinliklerini belirli kullanıcılarla veya içeriden risk rol gruplarıyla kısıtlaması da gerekebilir. Her öncelikli kullanıcı grubu için kullanıcıları, uyarıları, servis taleplerini ve raporları gözden geçirmek için tek tek kullanıcılar ve rol grupları atamayı seçebilirsiniz. Öncelikli kullanıcı grupları yerleşik *Insider Risk Yönetimi*, *Insider Risk Yönetimi Analistleri ve Insider Risk Yönetimi* *Araştırmacıları* rol gruplarına, bu rol gruplarından birine veya daha fazlasına ya da özel bir kullanıcı seçimine atanmış gözden geçirme izinlerine sahip olabilir.

Örneğin, kullanıcıların hassas bilgilere eriştiği çok gizli bir proje için veri sızıntılarına karşı korumanız gerekir. Kuruluşunuzda bu proje üzerinde çalışan kullanıcılar için *Gizli Project* *Kullanıcılar* öncelikli kullanıcı grubu oluşturmayı seçersiniz. Ayrıca, bu öncelikli kullanıcı grubunun, grupla ilişkilendirilmiş kullanıcıları, uyarıları, durumları ve raporları varsayılan şirket içi risk yönetimi yöneticileri, analistleri ve araştırmacıları tarafından görülemez. **Ayarlar'da** *Gizli Project Kullanıcılar* öncelikli kullanıcılar grubunu oluşturur ve grupla ilgili verileri görüntüleyebilen iki kullanıcıyı gözden geçiren olarak atarsınız. İlke sihirbazını ve *Öncelikli kullanıcılara göre veri sızıntıları* ilke şablonunu kullanarak yeni bir ilke oluşturur ve *gizli Project Kullanıcılar* öncelikli kullanıcılar grubunu ilkeye atarsınız. *Gizli Project Kullanıcılar* öncelikli kullanıcı grubu üyeleri için ilke tarafından incelenen etkinlikler risklere karşı daha hassastır ve bu kullanıcıların etkinliklerinin bir uyarı oluşturma ve daha yüksek önem düzeyine sahip uyarılara sahip olma olasılığı daha yüksektir.

### <a name="create-a-priority-user-group"></a>Öncelikli kullanıcı grubu oluşturma

Yeni bir öncelikli kullanıcı grubu oluşturmak için, Microsoft Purview uyumluluk portalındaki **Insider risk yönetimi** çözümünde ayar denetimlerini kullanacaksınız. Öncelikli bir kullanıcı grubu oluşturmak için *Insider Risk Management* veya *Insider Risk Management Yönetici* rol grubunun üyesi olmanız gerekir.

Öncelik kullanıcı grubu oluşturmak için aşağıdaki adımları tamamlayın:

1. [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com) **Insider risk yönetimi'ne** gidin ve **Insider risk ayarları'nı** seçin.
2. **Öncelik kullanıcı grupları (önizleme)** sayfasını seçin.
3. Grup oluşturma sihirbazını başlatmak için **Öncelik kullanıcı grupları (önizleme)** sayfasında **Öncelikli kullanıcı grubu oluştur'u** seçin.
4. **Ad ve açıklama** sayfasında aşağıdaki alanları doldurun:
    - **Ad (gerekli)**: Öncelikli kullanıcı grubu için kolay bir ad girin. Sihirbazı tamamladıktan sonra öncelikli kullanıcı grubunun adını değiştiremezsiniz.
    - **Açıklama (isteğe bağlı)**: Öncelikli kullanıcı grubu için bir açıklama girin.
5. Devam etmek için **İleri'yi** seçin.
6. **Üyeleri seçin** sayfasında, Aranacak **üyeleri seçin'i** seçin ve gruba hangi posta özellikli kullanıcı hesaplarının dahil olduğunu seçin veya Kuruluşunuzdaki tüm kullanıcıları gruba eklemek için **Tümünü seç** onay kutusunu seçin. Devam etmek için **Ekle'yi** veya gruba kullanıcı eklemeden kapatmak için **İptal'i** seçin.
7. Devam etmek için **İleri'yi** seçin.
8. **Bu grubu kimlerin görüntüleyebileceğini seçin** sayfasında, öncelikli kullanıcı grubu için kullanıcıları, uyarıları, servis taleplerini ve raporları kimlerin gözden geçirebileceğini tanımlamanız gerekir. En az bir kullanıcı veya içeriden risk yönetimi rol grubu atanmalıdır. **Kullanıcıları ve rol gruplarını seçin'i** seçin ve öncelik kullanıcı grubuna atamak istediğiniz kullanıcıları veya içeriden risk yönetimi rol gruplarını seçin. Seçili kullanıcıları veya rol gruplarını gruba atamak için **Ekle'yi** seçin.
9. Devam etmek için İleri'yi seçin.
10. **Gözden Geçir** sayfasında, öncelik kullanıcı grubu için seçtiğiniz ayarları gözden geçirin. Grup değerlerinden herhangi birini değiştirmek için **Düzenle** bağlantılarını seçin veya öncelikli kullanıcı grubunu oluşturup etkinleştirmek için **Gönder'i** seçin.
11. Sihirbazdan çıkmak için onay sayfasında **Bitti'yi** seçin.

### <a name="update-a-priority-user-group"></a>Öncelikli kullanıcı grubunu güncelleştirme

Mevcut öncelikli kullanıcı grubunu güncelleştirmek için Microsoft Purview uyumluluk portalındaki **Insider risk yönetimi** çözümünde ayar denetimlerini kullanacaksınız. Öncelikli bir kullanıcı grubunu güncelleştirmek için *Insider Risk Management* veya *Insider Risk Management Yönetici* rol grubunun üyesi olmanız gerekir.

Öncelik kullanıcı grubunu düzenlemek için aşağıdaki adımları tamamlayın:

1. [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com) **Insider risk yönetimi'ne** gidin ve **Insider risk ayarları'nı** seçin.
2. **Öncelik kullanıcı grupları (önizleme)** sayfasını seçin.
3. Düzenlemek istediğiniz öncelikli kullanıcı grubunu seçin ve **grubu düzenle'yi** seçin.
4. **Ad ve açıklama** sayfasında, gerekirse Açıklama alanını güncelleştirin. Öncelikli kullanıcı grubunun adını güncelleştiremezsiniz. Devam etmek için **İleri'yi** seçin.
5. **Üyeleri seçin** sayfasında Üye seç denetimini kullanarak gruba yeni **üyeler** ekleyin. Bir kullanıcıyı gruptan kaldırmak için kaldırmak istediğiniz kullanıcının yanındaki 'X' öğesini seçin. Devam etmek için **İleri'yi** seçin.
6. **Bu grubu kimlerin görüntüleyebileceğini seçin** sayfasında, öncelikli kullanıcı grubu için kullanıcıları, uyarıları, servis taleplerini ve raporları gözden geçirebilecek kullanıcıları veya rol gruplarını ekleyin veya kaldırın.
7. Devam etmek için **İleri'yi** seçin.
8. **Gözden Geçir** sayfasında, öncelikli kullanıcı grubu için seçtiğiniz güncelleştirme ayarlarını gözden geçirin. Grup değerlerinden herhangi birini değiştirmek için **Düzenle** bağlantılarını seçin veya öncelikli kullanıcı grubunu güncelleştirmek için **Gönder'i** seçin.
9. Sihirbazdan çıkmak için onay sayfasında **Bitti'yi** seçin.

### <a name="delete-a-priority-user-group"></a>Öncelikli kullanıcı grubunu silme

Mevcut öncelikli kullanıcı grubunu silmek için Microsoft Purview uyumluluk portalındaki **Insider risk yönetimi** çözümünde ayar denetimlerini kullanacaksınız. Öncelikli bir kullanıcı grubunu silmek için *Insider Risk Management* veya *Insider Risk Management Yönetici* rol grubunun üyesi olmanız gerekir.

> [!IMPORTANT]
> Öncelikli bir kullanıcı grubunun silinmesi, bu grubu atandığı tüm etkin ilkelerden kaldırır. Etkin bir ilkeye atanan öncelikli bir kullanıcı grubunu silerseniz, ilke kapsam içi kullanıcı içermez ve etkin bir şekilde boşta kalır ve uyarı oluşturmaz.

Öncelikli kullanıcı grubunu silmek için aşağıdaki adımları tamamlayın:

1. [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com) **Insider risk yönetimi'ne** gidin ve **Insider risk ayarları'nı** seçin.
2. **Öncelik kullanıcı grupları (önizleme)** sayfasını seçin.
3. Düzenlemek istediğiniz öncelikli kullanıcı grubunu seçin ve pano menüsünde **Sil'i** seçin.
4. **Sil** iletişim kutusunda **Evet'i** seçerek öncelikli kullanıcı grubunu silin veya **panoya dönmek için İptal'i** seçin.

## <a name="priority-physical-assets-preview"></a>Öncelikli fiziksel varlıklar (önizleme)

Öncelikli fiziksel varlıklara erişimi belirlemek ve erişim etkinliğini kullanıcı olaylarıyla ilişkilendirmek, uyumluluk altyapınızın önemli bir bileşenidir. Bu fiziksel varlıklar, kuruluşunuzdaki şirket binaları, veri merkezleri veya sunucu odaları gibi öncelikli konumları temsil eder. Insider risk etkinlikleri, olağan dışı saatlerde çalışan, bu yetkisiz hassas veya güvenli alanlara erişmeye çalışan kullanıcılarla ve meşru ihtiyaçları olmayan üst düzey alanlara erişim istekleriyle ilişkilendirilebilir.

Öncelikli fiziksel varlıklar etkinleştirildiğinde ve [Fiziksel badging veri bağlayıcısı](import-physical-badging-data.md) yapılandırıldığında, insider risk yönetimi fiziksel denetim ve erişim sistemlerinizden gelen sinyalleri diğer kullanıcı riski etkinlikleriyle tümleştirir. Fiziksel erişim sistemleri genelindeki davranış düzenlerini inceleyerek ve bu etkinlikleri diğer iç risk olaylarıyla ilişkilendirerek, iç risk yönetimi uyumluluk araştırmacılarının ve analistlerin uyarılar için daha bilinçli yanıt kararları almasına yardımcı olabilir. Öncelikli fiziksel varlıklara erişim puanlanmış ve öncelikli olmayan varlıklara erişimden farklı içgörülerde tanımlanmıştır.

Örneğin, kuruluşunuzun normal çalışma ve hassas proje alanlarına fiziksel erişimi izleyen ve onaylayan kullanıcılar için bir badging sistemi vardır. Hassas bir proje üzerinde çalışan birkaç kullanıcınız var ve bu kullanıcılar proje tamamlandığında kuruluşunuzun diğer alanlarına geri dönecektir. Hassas proje tamamlanmaya yaklaştığından, proje çalışmasının gizli kaldığından ve proje alanlarına erişimin sıkı bir şekilde denetlendiğinden emin olmak istiyorsunuz.

fiziksel badging sisteminizden erişim bilgilerini içeri aktarmak ve şirket içi risk yönetimindeki öncelikli fiziksel varlıkları belirtmek için Microsoft 365 fiziksel bağlantı veri bağlayıcısını etkinleştirmeyi seçersiniz. Kimlik doğrulama sisteminizden bilgileri içeri aktararak ve fiziksel erişim bilgilerini şirket içi risk yönetiminde tanımlanan diğer risk etkinlikleriyle ilişkilendirerek, projedeki kullanıcılardan birinin normal çalışma saatlerinden sonra proje ofislerine eriştiğini ve aynı zamanda normal çalışma alanlarından kişisel bulut depolama hizmetine büyük miktarda veri aktardığını fark ediyorsunuz. Çevrimiçi etkinlikle ilişkili bu fiziksel erişim etkinliği olası veri hırsızlığına işaret edebilir ve uyumluluk araştırmacıları ve analistleri bu kullanıcının koşulları tarafından belirlenen uygun eylemleri gerçekleştirebilir.

![Insider risk yönetimi öncelikli fiziksel varlıklar.](../media/insider-risk-settings-priority-assets.png)

### <a name="configure-priority-physical-assets"></a>Öncelikli fiziksel varlıkları yapılandırma

Öncelikli fiziksel varlıkları yapılandırmak için Fiziksel bağlantı bağlayıcısını yapılandıracak ve Microsoft Purview uyumluluk portalındaki **Insider risk yönetimi** çözümünde ayar denetimlerini kullanacaksınız. Öncelikli fiziksel varlıkları yapılandırmak için *Insider Risk Management* veya *Insider Risk Management Yöneticisi rol grubunun* üyesi olmanız gerekir.

Öncelikli fiziksel varlıkları yapılandırmak için aşağıdaki adımları tamamlayın:

1. Insider risk yönetimine başlama makalesindeki [insider risk yönetimi](insider-risk-management-configure.md) için yapılandırma adımlarını izleyin. 3. Adım'da Fiziksel badging bağlayıcısını yapılandırdığınızdan emin olun.

    > [!IMPORTANT]
    > Şirket içi risk yönetimi ilkelerinin, ayrılan ve sonlandırılan kullanıcılarla ilgili sinyal verilerini fiziksel denetim ve erişim platformlarınızdan gelen olay verileriyle ilişkilendirmesi için, Microsoft 365 İk bağlayıcısını da yapılandırmanız gerekir. Microsoft 365 İk bağlayıcısını etkinleştirmeden Fiziksel bağlantı bağlayıcısını etkinleştirirseniz, insider risk yönetimi ilkeleri yalnızca kuruluşunuzdaki kullanıcıların fiziksel erişim etkinliklerine yönelik olayları işler.

2. [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com) **Insider risk yönetimi'ne** gidin ve **Insider risk** **ayarlarıGizlilik** >  fiziksel varlıkları'nı seçin.
3. **Öncelik fiziksel varlıkları** sayfasında, Fiziksel badging bağlayıcısı tarafından içeri aktarılan varlık olayları için izlemek istediğiniz fiziksel varlık kimliklerini el ile ekleyebilir veya Fiziksel bağlama bağlayıcısı tarafından içeri aktarılan tüm fiziksel varlık kimliklerinin .csv dosyasını içeri aktarabilirsiniz: a) Fiziksel varlık kimliklerini el ile eklemek için **Öncelik fiziksel varlıkları ekle'yi** seçin,  bir fiziksel varlık kimliği girin ve **Ekle'yi** seçin. Diğer fiziksel varlık kimliklerini girin ve girilen tüm varlıkları kaydetmek için **Öncelik fiziksel varlıkları ekle'yi** seçin.
    b) bir .csv dosyasından fiziksel varlık kimliklerinin listesini eklemek için **Öncelikli fiziksel varlıkları içeri aktar'ı** seçin. Dosya gezgini iletişim kutusunda içeri aktarmak istediğiniz .csv dosyasını ve ardından **Aç'ı** seçin. .csv dosyalarındaki fiziksel varlık kimlikleri listeye eklenir.
4. **Ayarlar'da** **İlke göstergeleri** sayfasına gidin.
5. **İlke göstergeleri** sayfasında **Fiziksel erişim göstergeleri** bölümüne gidin ve **sonlandırma veya hassas varlığa başarısız erişimden sonra fiziksel erişim** onay kutusunu seçin.
6. Yapılandırmak ve çıkmak için **Kaydet'i** seçin.

### <a name="delete-a-priority-physical-asset"></a>Öncelikli fiziksel varlığı silme

Mevcut öncelikli fiziksel varlığı silmek için Microsoft Purview uyumluluk portalındaki Insider risk yönetimi çözümünde ayar denetimlerini kullanacaksınız. Öncelikli bir fiziksel varlığı silmek için Insider Risk Management veya Insider Risk Management Yöneticisi rol grubunun üyesi olmanız gerekir.

> [!IMPORTANT]
> Öncelikli bir fiziksel varlığın silinmesi, daha önce dahil edildiği tüm etkin ilkeler tarafından incelemeden kaldırılır. Öncelikli fiziksel varlıkla ilişkili etkinlikler tarafından oluşturulan uyarılar silinmez.

Öncelikli fiziksel varlığı silmek için aşağıdaki adımları tamamlayın:

1. [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com) **Insider risk yönetimi'ne** gidin ve **Insider risk** **ayarlarıGizlilik** >  fiziksel varlıkları'nı seçin.
2. **Öncelik fiziksel varlıkları** sayfasında, silmek istediğiniz varlığı seçin.
3. Varlığı silmek için eylem menüsünde Sil'i **seçin.**

## <a name="power-automate-flows-preview"></a>Power Automate akışları (önizleme)

[Microsoft Power Automate](/power-automate/getting-started), uygulamalar ve hizmetler genelinde eylemleri otomatik hale getiren bir iş akışı hizmetidir. Şablonlardan gelen veya el ile oluşturulan akışları kullanarak, bu uygulama ve hizmetlerle ilişkili ortak görevleri otomatikleştirebilirsiniz. insider risk yönetimi için Power Automate akışlarını etkinleştirdiğinizde, servis talepleri ve kullanıcılar için önemli görevleri otomatikleştirebilirsiniz. Kullanıcı, uyarı ve servis talebi bilgilerini almak ve bu bilgileri paydaşlarla ve diğer uygulamalarla paylaşmak için Power Automate akışlarını yapılandırabilir, ayrıca iç risk yönetimindeki eylemleri otomatikleştirebilirsiniz(örneğin, servis talebi notlarına gönderme). Power Automate akışları, ilke kapsamındaki durumlar ve tüm kullanıcılar için geçerlidir.

Insider risk yönetimi içeren Microsoft 365 abonelikleri olan müşterilerin önerilen insider risk yönetimi Power Automate şablonlarını kullanmak için ek Power Automate lisanslarına ihtiyacı yoktur. Bu şablonlar kuruluşunuzu destekleyecek şekilde özelleştirilebilir ve temel insider risk yönetimi senaryolarını kapsar. Bu şablonlardaki premium Power Automate özelliklerini kullanmayı, Microsoft Purview bağlayıcısını kullanarak özel bir şablon oluşturmayı veya Microsoft 365'deki diğer uyumluluk alanları için Power Automate şablonları kullanmayı seçerseniz daha fazla Power Automate lisansına ihtiyacınız olabilir.

Aşağıdaki Power Automate şablonları, müşterilere şirket içi risk yönetimi kullanıcıları ve durumları için işlem otomasyonunu desteklemek üzere sağlanır:

- **Şirket içi risk ilkesine eklendiklerinde kullanıcıları bilgilendirin**: Bu şablon, iç ilkeleri, gizlilik veya mevzuat gereksinimleri olan kuruluşlara yöneliktir ve iç risk yönetimi ilkelerine tabi olduklarında kullanıcılara bildirim verilmesi gerekir. Bu akış, **Kullanıcılar** sayfasında bir kullanıcı için yapılandırılıp seçildiğinde, kullanıcı bir insider risk yönetimi ilkesine eklendiğinde kullanıcılara ve yöneticilerine bir e-posta iletisi gönderilir. Bu şablon, tarih/saat ve ileti alıcısı gibi bildirim iletisi ayrıntılarını izlemeye yardımcı olmak için SharePoint sitede barındırılan bir SharePoint listesinin güncelleştirilmesini de destekler. **Gizlilik ayarlarında** kullanıcıları anonimleştirmeyi seçtiyseniz, bu şablondan oluşturulan akışlar kullanıcı gizliliğinin korunması için amaçlandığı gibi çalışmaz. Bu şablonu kullanan Power Automate akışları **Kullanıcılar panosunda** kullanılabilir.
- **şirket içi risk durumundaki bir kullanıcı hakkında İk'dan veya işletmeden bilgi isteme**: Bir olay üzerinde hareket ederken, iç risk analistlerinin ve araştırmacıların olay etkinliklerinin bağlamını anlamak için İk'ya veya diğer paydaşlara danışması gerekebilir. Bu akış bir servis talebi için yapılandırılıp seçildiğinde, analistler ve araştırmacılar bu akış için yapılandırılmış İk ve iş paydaşlarına bir e-posta iletisi gönderir. Her alıcıya önceden yapılandırılmış veya özelleştirilebilir yanıt seçenekleri içeren bir ileti gönderilir. Alıcılar bir yanıt seçeneği seçtiğinde, yanıt servis talebi notu olarak kaydedilir ve alıcı ile tarih/saat bilgilerini içerir. **Gizlilik ayarlarında** kullanıcıları anonimleştirmeyi seçtiyseniz, bu şablondan oluşturulan akışlar kullanıcı gizliliğinin korunması için amaçlandığı gibi çalışmaz. Bu şablonu kullanan Power Automate akışları **Servis Talepleri panosunda** kullanılabilir.
- **Bir kullanıcının içeriden risk uyarısı olduğunda yöneticiye bildirme**: Bir kullanıcının içeriden risk yönetimi uyarısı olduğunda bazı kuruluşların anında yönetim bildirimine sahip olması gerekebilir. Bu akış yapılandırılıp seçildiğinde, servis talebi kullanıcısının yöneticisine tüm servis talebi uyarıları hakkında aşağıdaki bilgileri içeren bir e-posta iletisi gönderilir:
    - Uyarı için geçerli ilke
    - Uyarının tarih/saati
    - Uyarının önem derecesi düzeyi

    Akış, iletinin gönderildiğine ve akışın etkinleştirildiğine ilişkin servis talebi notlarını otomatik olarak güncelleştirir. **Gizlilik ayarlarında** kullanıcıları anonimleştirmeyi seçtiyseniz, bu şablondan oluşturulan akışlar kullanıcı gizliliğinin korunması için amaçlandığı gibi çalışmaz. Bu şablonu kullanan Power Automate akışları **Servis Talepleri panosunda** kullanılabilir.
- **ServiceNow'da insider risk olayı için kayıt oluşturma**: Bu şablon, iç risk yönetimi durumlarını izlemek için ServiceNow çözümünü kullanmak isteyen kuruluşlara yöneliktir.  Bir durumda, insider risk analistleri ve araştırmacıları ServiceNow'da olay için bir kayıt oluşturabilir. Bu şablonu özelleştirerek ServiceNow'daki seçili alanları kuruluşunuzun gereksinimlerine göre doldurabilirsiniz. Bu şablonu kullanan Power Automate akışları **Servis Talepleri panosunda** kullanılabilir. Kullanılabilir ServiceNow alanları hakkında daha fazla bilgi için [ServiceNow Bağlayıcısı başvuru](/connectors/service-now/) makalesine bakın.

### <a name="create-a-power-automate-flow-from-insider-risk-management-template"></a>Insider risk yönetimi şablonundan Power Automate akışı oluşturma

Önerilen bir insider risk yönetimi şablonundan Power Automate akışı oluşturmak için, Microsoft Purview uyumluluk portalındaki **Insider risk yönetimi** çözümündeki ayarlar denetimlerini veya Doğrudan **Servis Talepleri** veya **Kullanıcılar panolarında** çalışırken **Otomatikleştirme** denetiminin **Power Automate akışlarını yönet** seçeneğini kullanacaksınız.

Ayarlar alanında bir Power Automate akışı oluşturmak için *Insider Risk Management* veya *Insider Risk Management Yöneticisi* rol grubunun üyesi olmanız gerekir. **Power Automate akışlarını yönet seçeneğiyle bir Power Automate akışı** oluşturmak için, en az bir iç risk yönetimi rol grubunun üyesi olmanız gerekir.

Önerilen bir insider risk yönetimi şablonundan Power Automate akışı oluşturmak için aşağıdaki adımları tamamlayın:

1. [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com) **Insider risk yönetimi'ne** gidin ve **Insider risk ayarları** >  **Power Automate akışları'nı** seçin. Ayrıca **, AutomateManage** >  Power Automate akışlarını seçerek **Servis Talepleri** veya **Kullanıcılar panoları** **sayfalarından** da erişebilirsiniz.
2. **Power Automate akışları** sayfasında, sayfadaki **Insider risk yönetimi şablonları** bölümünden önerilen bir şablon seçin.
3. Akış, akış için gereken ekli bağlantıları listeler ve bağlantı durumlarının kullanılabilir olup olmadığını not eder. Gerekirse, kullanılabilir olarak görüntülenmemiş bağlantıları güncelleştirin. **Devam**'ı seçin.
4. Varsayılan olarak, önerilen akışlar önerilen iç risk yönetimiyle önceden yapılandırılır ve akış için atanan görevi tamamlamak için gereken hizmet verileri alanlarını Microsoft 365. Gerekirse Gelişmiş **seçenekleri göster** denetimini kullanarak ve akış bileşeni için kullanılabilir özellikleri yapılandırarak akış bileşenlerini özelleştirin.
5. Gerekirse **, Yeni adım** düğmesini seçerek akışa başka adımlar ekleyin. Çoğu durumda, önerilen varsayılan şablonlar için bu gerekli olmamalıdır.
6. Akışı daha fazla yapılandırma için kaydetmek için **Taslağı kaydet'i** veya akışın yapılandırmasını tamamlamak için **Kaydet'i** seçin.
7. **Power Automate akışı** sayfasına dönmek için **Kapat'ı** seçin. Yeni şablon **Akışlarım** sekmelerinde akış olarak listelenir ve akışı oluşturan kullanıcı için insider risk yönetimi örnekleriyle çalışırken **Otomatikleştirme** açılan denetiminden otomatik olarak kullanılabilir.

> [!IMPORTANT]
> Kuruluşunuzdaki diğer kullanıcıların akışa erişmesi gerekiyorsa akışın paylaşılması gerekir.

### <a name="create-a-custom-power-automate-flow-for-insider-risk-management"></a>Insider risk yönetimi için özel Power Automate akışı oluşturma

Kuruluşunuz için bazı işlemler ve iş akışları önerilen insider risk yönetimi akışı şablonlarının dışında olabilir ve içeriden risk yönetimi alanları için özel Power Automate akışları oluşturmanız gerekebilir. Power Automate akışları esnektir ve kapsamlı özelleştirmeyi destekler, ancak insider risk yönetimi özellikleriyle tümleştirmek için izlenmesi gereken adımlar vardır.

Insider risk yönetimi için özel bir Power Automate şablonu oluşturmak için aşağıdaki adımları tamamlayın:

1. **Power Automate akış lisansınızı denetleyin**: Insider risk yönetimi tetikleyicilerini kullanan özelleştirilmiş Power Automate akışları oluşturmak için bir Power Automate lisansına ihtiyacınız vardır. Önerilen insider risk yönetimi akışı şablonları fazladan lisans gerektirmez ve insider risk yönetimi lisansınızın bir parçası olarak dahil edilir.
2. **Otomatik akış oluşturma**: Bir iç risk yönetimi olayı tarafından tetiklenen bir veya daha fazla görevi gerçekleştiren bir akış oluşturun. Otomatik akış oluşturma hakkında ayrıntılı bilgi için bkz. [Power Automate'de akış oluşturma](/power-automate/get-started-logic-flow).
3. **Microsoft Purview bağlayıcısını seçin**: Microsoft Purview bağlayıcısını arayın ve seçin. Bu bağlayıcı, iç risk yönetimi tetikleyicilerini ve eylemlerini etkinleştirir. Bağlayıcılar hakkında daha fazla bilgi için [Bağlayıcı başvurusuna genel bakış](/connectors/connector-reference/) makalesine bakın.
4. **Akışınız için insider risk yönetimi tetikleyicilerini seçin**: Insider risk yönetiminin özel Power Automate akışları için kullanılabilir iki tetikleyicisi vardır:
    - **Seçilen bir insider risk yönetimi olayı için**: Bu tetikleyiciye sahip akışlar, insider risk yönetimi Durumları pano sayfasından seçilebilir.
    - **Seçili bir insider risk yönetimi kullanıcısı için**: Bu tetikleyiciye sahip akışlar, insider risk yönetimi Kullanıcıları panosu sayfasından seçilebilir.
5. Akışınız için insider risk yönetimi eylemlerini seçin: Insider risk yönetiminin özel akışınıza dahil etmek üzere çeşitli eylemler arasından seçim yapabilirsiniz:
    - Insider risk yönetimi uyarısı alma
    - Insider risk yönetimi olayı alma
    - Insider risk yönetimi kullanıcılarını alma
    - Bir servis talebi için insider risk yönetimi uyarıları alma
    - Insider risk yönetimi servis talebi notu ekleme

### <a name="share-a-power-automate-flow"></a>Power Automate akışı paylaşma

Varsayılan olarak, bir kullanıcı tarafından oluşturulan Power Automate akışları yalnızca o kullanıcı tarafından kullanılabilir. Diğer insider risk yönetimi kullanıcılarının bir akışa erişmesi ve akış kullanması için akışın akış oluşturucusu tarafından paylaşılması gerekir. Bir akışı paylaşmak için Microsoft Purview uyumluluk portalındaki **Insider risk yönetimi çözümündeki** ayarlar denetimlerini veya Doğrudan **Servis Talepleri** veya **Kullanıcılar pano** sayfalarında çalışırken Otomatikleştirme denetimindeki **Power Automate akışlarını yönet** seçeneğini kullanacaksınız. Bir akışı paylaştıktan sonra, akışın paylaşıldığı herkes **Servis Talebi** ve **Kullanıcı panolarındaki** **Otomatikleştirme** denetimi açılan listesinde akışa erişebilir.

Ayarlar alanında bir Power Automate akışını paylaşmak için *Insider Risk Management* veya *Insider Risk Management Yöneticisi* rol grubunun üyesi olmanız gerekir. Power Automate akışı **Power Automate akışlarını yönet** seçeneğiyle paylaşmak için en az bir iç risk yönetimi rol grubunun üyesi olmanız gerekir.

Power Automate akışını paylaşmak için aşağıdaki adımları tamamlayın:

1. [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com) **Insider risk yönetimi'ne** gidin ve **Insider risk ayarları** >  **Power Automate akışları'nı** seçin. Ayrıca **, AutomateManage** >  Power Automate akışlarını seçerek **Servis Talepleri** veya **Kullanıcılar panoları** **sayfalarından** da erişebilirsiniz.
2. **Power Automate akışları** sayfasında **Akışlarım** veya **Ekip akışları** sekmesini seçin.
3. Paylaşacak akışı seçin ve ardından akış seçenekleri menüsünden **Paylaş'ı** seçin.
4. Akış paylaşımı sayfasında, akışın sahibi olarak eklemek istediğiniz kullanıcı veya grubun adını girin.
5. **Bağlantı Kullanıldı** iletişim kutusunda **Tamam'ı** seçerek eklenen kullanıcı veya grubun akışa tam erişimi olacağını kabul edin.

### <a name="edit-a-power-automate-flow"></a>Power Automate akışını düzenleme

Bir akışı düzenlemek için, Microsoft Purview uyumluluk portalındaki **Insider risk yönetimi** çözümündeki ayarlar denetimlerini veya Doğrudan **Servis Talepleri** veya **Kullanıcılar panolarında** çalışırken **Otomatikleştirme** denetimindeki **Power Automate akışlarını yönet** seçeneğini kullanacaksınız.

Ayarlar alanında bir Power Automate akışını düzenlemek için *Insider Risk Management* veya *Insider Risk Management Yöneticisi* rol grubunun üyesi olmanız gerekir. Power Automate akışını **Power Automate akışlarını yönet** seçeneğiyle düzenlemek için en az bir iç risk yönetimi rol grubunun üyesi olmanız gerekir.

Power Automate akışını düzenlemek için aşağıdaki adımları tamamlayın:

1. [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com) **Insider risk yönetimi'ne** gidin ve **Insider risk ayarları** >  **Power Automate akışları'nı** seçin. Ayrıca **, AutomateManage** >  Power Automate akışlarını seçerek **Servis Talepleri** veya **Kullanıcılar panoları** **sayfalarından** da erişebilirsiniz.
2. **Power Automate akışlar** sayfasında düzenlemek üzere bir akış seçin ve akış denetimi menüsünden **Düzenle'yi** seçin.
3. Bir akış bileşeni ayarını değiştirmek için **üç nokta** >  **Ayarlar** veya bir akış bileşenini silmek için **üç** >  **noktaDele** seçeneğini belirleyin.
4. Akışı düzenlemeyi tamamlamak için **Kaydet'i** ve ardından **Kapat'ı** seçin.

### <a name="delete-a-power-automate-flow"></a>Power Automate akışını silme

Bir akışı silmek için Microsoft Purview uyumluluk portalındaki **Insider risk yönetimi** çözümündeki ayarlar denetimlerini veya Doğrudan **Servis Talepleri** veya **Kullanıcılar panolarında** çalışırken **Otomatikleştirme** denetimindeki **Power Automate akışlarını yönet** seçeneğini kullanacaksınız. Bir akış silindiğinde, tüm kullanıcılar için bir seçenek olarak kaldırılır.

Ayarlar alanındaki bir Power Automate akışını silmek için *Insider Risk Management* veya *Insider Risk Management Yöneticisi* rol grubunun üyesi olmanız gerekir. **Power Automate akışlarını yönet seçeneğiyle bir Power Automate akışını** silmek için, en az bir iç risk yönetimi rol grubunun üyesi olmanız gerekir.

Power Automate akışını silmek için aşağıdaki adımları tamamlayın:

1. [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com) **Insider risk yönetimi'ne** gidin ve **Insider risk ayarları** >  **Power Automate akışları'nı** seçin. Ayrıca **, AutomateManage** >  Power Automate akışlarını seçerek **Servis Talepleri** veya **Kullanıcılar panoları** **sayfalarından** da erişebilirsiniz.
2. **Power Automate akışlar** sayfasında, silinecek bir akış seçin ve akış denetimi menüsünden **Sil'i** seçin.
3. Silme onayı iletişim kutusunda Akışı kaldırmak için **Sil'i** seçin veya silme eyleminden çıkmak için **İptal'i** seçin.

## <a name="microsoft-teams-preview"></a>Microsoft Teams (önizleme)

Uyumluluk analistleri ve araştırmacıları, Microsoft Teams iç risk yönetimi olaylarında işbirliği için kolayca kullanabilir. Microsoft Teams'deki diğer paydaşları koordine edebilir ve bunlarla iletişim kurabilirler:

- Özel Teams kanallarındaki durumlar için yanıt etkinliklerini koordine edin ve gözden geçirin
- Tek tek davalarla ilgili dosyaları ve kanıtları güvenli bir şekilde paylaşma ve depolama
- Analistlerin ve araştırmacıların yanıt etkinliklerini izleme ve gözden geçirme

Microsoft Teams insider risk yönetimi için etkinleştirildikten sonra, her uyarı onaylandığında ve bir servis talebi oluşturulduğunda ayrılmış bir Microsoft Teams ekibi oluşturulur. Ekip varsayılan olarak *Insider Risk Management*, *Insider Risk Management Analysts ve Insider Risk Management Araştırmacıları* rol gruplarının (en fazla 100 ilk kullanıcı) tüm üyelerini otomatik olarak içerir. Ekip oluşturulduktan sonra ve uygun şekilde ek kuruluş katkıda bulunanları eklenebilir. analistler ve araştırmacılar, Microsoft Teams etkinleştirilmeden önce oluşturulan mevcut durumlar için gerekirse bir durumda çalışırken yeni bir Microsoft Teams ekibi oluşturmayı tercih edebilir.  insider risk yönetiminde ilişkili olayı çözümledikten sonra ekip otomatik olarak arşivlendirilir (gizli ve salt okunur olarak taşınır).

Microsoft Teams'da ekiplerin ve kanalların nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [Microsoft Teams ekiplere ve kanallara genel bakış](/MicrosoftTeams/teams-channels-overview).

Servis talepleri için Microsoft Teams desteğinin etkinleştirilmesi hızlı ve kolay bir şekilde yapılandırılabilir. insider risk yönetimi için Microsoft Teams etkinleştirmek için aşağıdaki adımları tamamlayın:

1. [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com) **Insider risk** **yönetimiInsider** >  risk ayarları'na gidin.
2. **Microsoft Teams** sayfasını seçin.
3. insider risk yönetimi için Microsoft Teams tümleştirmesini etkinleştirin.
4. Yapılandırmak ve çıkmak için **Kaydet'i** seçin.

![Insider risk yönetimi Microsoft Teams.](../media/insider-risk-settings-teams.png)

### <a name="create-a-microsoft-teams-team-for-existing-cases"></a>Mevcut servis talepleri için Microsoft Teams ekibi oluşturma

Mevcut servis talepleriniz olduktan sonra insider risk yönetimi için Microsoft Teams desteğini etkinleştirirseniz, gerektiğinde her servis talebi için el ile bir ekip oluşturmanız gerekir. Insider risk yönetimi ayarlarında Microsoft Teams desteği etkinleştirdikten sonra, yeni servis talepleri otomatik olarak yeni bir Microsoft Teams ekibi oluşturur.

Kullanıcıların bir servis talebine Microsoft Teams ekibi oluşturmak için kuruluşunuzda Microsoft 365 grupları oluşturma iznine sahip olması gerekir. Microsoft 365 Grupları izinlerini yönetme hakkında daha fazla bilgi için bkz. [Microsoft 365 Grupları oluşturabilecek kişileri yönetme](../solutions/manage-creation-of-groups.md).

Bir servis talebi için ekip oluşturmak için, doğrudan mevcut bir durumda çalışırken Microsoft Ekibi Oluştur denetimini kullanacaksınız. Yeni bir ekip oluşturmak için aşağıdaki adımları tamamlayın:

1. [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com) **Insider risk** **yönetimiAralar'a** >  gidin ve mevcut bir servis talebini seçin.
2. Servis talebi eylem menüsünde **Microsoft Ekibi Oluştur'u** seçin.
3. **Ekip adı** alanına yeni Microsoft Teams ekibi için bir ad girin.
4. **Microsoft ekibi oluştur'u** ve ardından **Kapat'ı** seçin.

Insider risk yönetimi rol gruplarına atanan kullanıcı sayısına bağlı olarak, tüm araştırmacıların ve analistlerin bir olay için Microsoft Teams ekibine eklenmesi 15 dakika sürebilir.

## <a name="analytics"></a>Analytics

Insider risk analizi, herhangi bir iç risk ilkesi yapılandırmadan kuruluşunuzdaki olası insider risklerini değerlendirmenizi sağlar. Bu değerlendirme, kuruluşunuzun daha yüksek kullanıcı riski olan olası alanları belirlemesine yardımcı olabilir ve yapılandırmayı düşünebileceğiniz iç risk yönetimi ilkelerinin türünü ve kapsamını belirlemeye yardımcı olabilir. Analiz taramaları kuruluşunuz için aşağıdaki avantajları sunar:

- Yapılandırılması kolay: Analiz taramalarına başlamak için analiz önerisiyle istendiğinde Taramayı çalıştır'ı seçebilir veya **Insider risk** **ayarlarıAnalytics'e** >  gidip analizi etkinleştirebilirsiniz.
- Tasarıma göre gizlilik: Tarama sonuçları ve içgörüleri toplanmış ve anonimleştirilmiş kullanıcı etkinliği olarak döndürülür; tek tek kullanıcı adları gözden geçirenler tarafından tanımlanamaz.
- Birleştirilmiş içgörüler aracılığıyla olası riskleri anlama: Tarama sonuçları, kullanıcılarınız için olası risk alanlarını hızla belirlemenize ve bu riskleri azaltmaya yardımcı olmak için en iyi ilkeyi belirlemenize yardımcı olabilir.

Analizin olası insider risklerinin belirlenmesini hızlandırmaya ve hızla harekete geçmenize nasıl yardımcı olabileceğini anlamanıza yardımcı olması için [Insider Risk Management Analytics videosunu](https://www.youtube.com/watch?v=5c0P5MCXNXk) inceleyin.

Analiz, olası risk alanlarıyla ilgili içgörüleri belirlemeye yardımcı olmak için çeşitli kaynaklardan gelen risk etkinliği olaylarını tarar. Analiz, geçerli yapılandırmanıza bağlı olarak aşağıdaki alanlarda uygun risk etkinliklerini arar:

- **Microsoft 365 denetim günlükleri**: Tüm taramalara dahil edilen bu, riskli olabilecek etkinliklerin çoğunu tanımlamak için birincil kaynaktır.
- **Exchange Online**: Tüm taramalara dahil edilen Exchange Online etkinliği, eklerdeki verilerin dış kişilere veya hizmetlere e-postayla gönderildiği etkinlikleri tanımlamaya yardımcı olur.
- **Azure Active Directory**: Tüm taramalara dahil Azure Active Directory geçmişi, silinen kullanıcı hesaplarına sahip kullanıcılarla ilişkili riskli etkinlikleri tanımlamaya yardımcı olur.
- **İk veri bağlayıcısı Microsoft 365**: İk bağlayıcısı olayları yapılandırılırsa, istifa veya yaklaşan sonlandırma tarihleri olan kullanıcılarla ilişkili riskli etkinliklerin belirlenmesine yardımcı olur.

Taramalardan elde edilen analiz içgörüleri, hem tek hem de sıralı kullanıcı etkinliklerine dayalı olarak insider risk yönetimi ilkeleri ve rapor sonuçları tarafından kullanılan risk etkinliği sinyallerini temel alır. Ancak analiz için risk puanlaması 10 güne kadar etkinlik temelinde gerçekleşirken, iç risk ilkeleri içgörüler için günlük etkinlik kullanır. Kuruluşunuzda analizi ilk kez etkinleştirdiğinizde ve çalıştırdığınızda tarama sonuçlarını bir gün boyunca görürsünüz. Analizi etkin bırakırsanız, önceki 10 günlük etkinliğin maksimum aralığı için içgörü raporlarına eklenen her günlük taramanın sonuçlarını görürsünüz.

### <a name="enable-analytics-and-start-your-scan"></a>Analizi etkinleştirme ve taramanızı başlatma

Insider risk analizini etkinleştirmek için *Insider Risk Management*, *Insider Risk Management Yöneticisi* veya *Microsoft 365 Genel yönetici* rol grubunun üyesi olmanız gerekir.
Insider risk analizini etkinleştirmek için aşağıdaki adımları tamamlayın:

1. [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com) **Insider risk yönetimi'ne** gidin.
2. Insider risk yönetimine **Genel Bakış** sekmesinde **, Kuruluşunuzdaki insider risklerini tara** kartında **Tarama çalıştır'ı** seçin. Bu, kuruluşunuz için analiz taramasını açar. Ayrıca **Insider risk** **ayarlarıAnalytics'e** >  giderek ve **olası insider risklerini belirlemek için Kiracınızın kullanıcı etkinliğini tara seçeneğini etkinleştirerek de kuruluşunuzda taramayı** açabilirsiniz.
3. **Analiz ayrıntıları** bölmesinde **Taramayı çalıştır'ı** seçerek kuruluşunuz için taramayı başlatın. Analiz tarama sonuçlarının, içgörülerin gözden geçirilebilir raporlar olarak kullanılabilir hale gelmesi 48 saat kadar sürebilir.

![Insider risk yönetimi analiz ayarları.](../media/insider-risk-settings-analytics-enable.png)

### <a name="viewing-analytics-insights-and-creating-new-policies"></a>Analiz içgörülerini görüntüleme ve yeni ilkeler oluşturma

Kuruluşunuz için ilk analiz taraması tamamlandıktan sonra *, Insider Risk Management Yönetici* rol grubunun üyeleri otomatik olarak bir e-posta bildirimi alır ve kullanıcılarınız tarafından riskli olabilecek etkinliklere yönelik ilk içgörüleri ve önerileri görüntüleyebilir. Kuruluşunuz için analizi kapatmadığınız sürece günlük taramalar devam eder. Kuruluşunuzdaki ilk etkinlik örneğinden sonra analiz (veri sızıntıları, hırsızlık ve sızdırma) için üç kapsam içi kategorinin her biri için yöneticilere e-posta bildirimleri sağlanır. E-posta bildirimleri, günlük taramalardan kaynaklanan izleme etkinliği algılama için yöneticilere gönderilmez. **Insider risk yönetimi** >  **Ayarlar** >  **Analytics** özelliği devre dışı bırakılır ve kuruluşunuzda yeniden etkinleştirilirse, otomatik e-posta bildirimleri sıfırlanır ve yeni tarama içgörüleri için *Insider Risk Management Yönetici* rol grubunun üyelerine e-postalar gönderilir.

Kuruluşunuzun olası risklerini görüntülemek için **Genel Bakış** sekmesine gidin ve **Insider risk analizi** kartında **Sonuçları görüntüle'yi** seçin. Kuruluşunuz için tarama tamamlanamadıysa taramanın hala etkin olduğunu belirten bir ileti görürsünüz.

![Insider risk yönetimi analizi raporu hazır kartı.](../media/insider-risk-analytics-ready-card.png)

Tamamlanan taramalar için kuruluşunuzda bulunan olası riskleri ve bu riskleri ele almak için içgörüleri ve önerileri görürsünüz. Belirlenen riskler ve belirli içgörüler, alana göre gruplandırılmış raporlara, tanımlanan risklere sahip toplam kullanıcı sayısı, riskli olabilecek etkinlikleri olan bu kullanıcıların yüzdesi ve bu riskleri azaltmaya yardımcı olmak için önerilen iç risk ilkesine dahildir. Raporlar şunlardır:

- **Veri sızıntıları içgörüleri**: Tüm kullanıcılar için, kuruluşunuzun dışında yanlışlıkla fazla bilgi paylaşımı veya kötü amaçlı kullanıcılar tarafından veri sızıntıları içerebilen etkinlikler.
- **Veri hırsızlığı içgörüleri**: Ayrılan kullanıcılara veya silinmiş Azure Active Directory hesaplarına sahip kullanıcılara yönelik etkinlikler, kuruluşunuzun dışındaki bilgilerin riskli bir şekilde paylaşılması veya kötü amaçlı kullanıcılar tarafından veri çalınması olabilir.
- **En iyi sızdırma içgörüleri**: Tüm kullanıcıların kuruluşunuzun dışında veri paylaşımını içerebilecek etkinlikleri.

![Insider risk yönetimi analizine genel bakış raporu.](../media/insider-risk-analytics-overview.png)

Bir içgörüye ilişkin daha fazla bilgi görüntülemek için **Ayrıntıları görüntüle'yi** seçerek içgörüye ilişkin ayrıntılar bölmesini görüntüleyin. Ayrıntılar bölmesi, önerilen ilkeyi hızla oluşturmanıza yardımcı olmak için içgörü sonuçlarının tamamını, bir içgörü risk ilkesi önerisini ve **İlke oluştur** düğmesini içerir. İlke oluştur'u seçtiğinizde ilke sihirbazına yönlendirilirsiniz ve içgörüyle ilgili önerilen ilke şablonunu otomatik olarak seçersiniz. Örneğin analiz içgörüleri *Veri sızıntısı* etkinliğine yönelikse, ilke sihirbazında *sizin için Genel veri sızıntıları* ilke şablonu önceden seçilir.

![Insider risk yönetimi analiz ayrıntıları raporu.](../media/insider-risk-analytics-details.png)

### <a name="turn-off-analytics"></a>Analizi kapatma

Insider risk analizini kapatmak için *Insider Risk Management, Insider Risk Management* *Yöneticisi* veya Microsoft 365 *Genel yönetici* rol grubunun üyesi olmanız gerekir. Analizi devre dışı bırakdıktan sonra analiz içgörü raporları statik kalır ve yeni riskler için güncelleştirilmez.

Insider risk analizini kapatmak için aşağıdaki adımları tamamlayın:

1. [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com) **Insider risk yönetimi'ne** gidin.
2. **Insider risk** **ayarlarıAnalytics** >  sayfası'nı seçin.
3. **Analiz** sayfasında, **olası insider risklerini belirlemek için Kiracınızın kullanıcı etkinliğini tara** seçeneğini kapatın.

## <a name="admin-notifications"></a>Yönetici bildirimleri

Yönetici bildirimleri, seçilebilir iç risk yönetimi rol gruplarına otomatik olarak bir e-posta bildirimi gönderir. Bildirimleri etkinleştirebilir ve aşağıdaki senaryolar için hangi rol gruplarının bildirim alacağını atayabilirsiniz:

- Yeni bir ilke için ilk uyarı oluşturulduğunda bir bildirim e-postası gönderin. İlkeler, ilk kez yapılan uyarılar için 24 saatte bir kontrol edilir ve ilkenin sonraki uyarılarında bildirimler gönderilmez.
- Yeni yüksek önem derecesi uyarıları oluşturulduğunda günlük bir e-posta gönderin. İlkeler, yüksek önem dereceli uyarılar için 24 saatte bir denetlenmektedir.
- Çözümlenmemiş uyarıları olan ilkeleri özetleyen haftalık bir e-posta gönderme

Kuruluşunuz için insider risk yönetimi analizini etkinleştirdiyseniz, *Insider Risk Management Yönetici* rol grubunun üyeleri veri sızıntıları, hırsızlık ve sızdırma etkinlikleriyle ilgili ilk analiz içgörüleri için otomatik olarak bir e-posta bildirimi alır.

Yönetici ve analiz bildirimlerini devre dışı bırakmak isterseniz aşağıdaki adımları tamamlayın:

1. [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com) **Insider risk** **yönetimiInsider** >  risk ayarları'na gidin.
2. **Yönetici bildirimleri** sayfasını seçin.
3. Aşağıdaki seçeneklerin onay kutusunu uygun şekilde temizleyin:
    - **Yeni bir ilke için ilk uyarı oluşturulduğunda bildirim e-postası gönderme**
    - **Analytics'te yeni bir içgörü sağlandığında e-posta bildirimi gönderme**
    - **Analytics kapatıldığında e-posta bildirimi gönderme**

4. Yapılandırmak ve çıkmak için **Kaydet'i** seçin.
