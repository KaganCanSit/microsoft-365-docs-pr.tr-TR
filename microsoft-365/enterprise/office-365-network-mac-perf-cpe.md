---
title: Microsoft 365 bilgilendirilmiş ağ yönlendirme
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/06/2021
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Microsoft 365 bilgilendirilmiş ağ yönlendirme
ms.openlocfilehash: fc946b3a1de057605b89bcadeb4e5b7269aebcb0
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2022
ms.locfileid: "65622477"
---
# <a name="microsoft-365-informed-network-routing"></a>Microsoft 365 bilgilendirilmiş ağ yönlendirme

Bilgilendirilmiş ağ yönlendirme, Microsoft hizmet uç noktalarına ağ bağlantınızı iyileştirmek ve iyileştirmek için çeşitli Microsoft 365 uygulamalarını üçüncü taraf yazılım tanımlı ağ (SD-WAN) çözümleriyle tümleştiren bir özelliktir. İyileştirilmiş SD-WAN bağlantısı, kullanıcı deneyimlerinin ve performansının iyileştirilmesine neden olabilir.

## <a name="overview"></a>Genel bakış

Bilgilendirilmiş ağ yönlendirmesi, Microsoft ile SD-WAN çözümünüz arasında çift yönlü bir veri paylaşım kanalı sağlar. Yapılandırdığınız her ofis konumu ve İnternet bağlantı hattı için Microsoft, belirli bir İnternet bağlantı hattıyla ilişkili ağ trafiği için seçilen Microsoft 365 uygulama deneyimlerinin kalitesi hakkında SD-WAN çözümüyle düzenli aralıklarla geri bildirim paylaşır. Bu geri bildirimi kullanarak SD-WAN çözümü, uygulama trafiğini alternatif kullanılabilir bağlantılar aracılığıyla yönlendirmek Microsoft 365 akıllı kurtarma eylemleri gerçekleştirebilir. 

Belirli bir İnternet bağlantı hattı yolundaki artan gecikme süresi veya yüksek paket kaybı gibi hizmet kalitesinin sürekli olarak algılanması zordur. Bu düşüşler Exchange Online, SharePoint, OneDrive ve Microsoft Teams gibi uygulamalar için kullanıcı deneyimlerine zarar verebilir. Yaygın belirtiler arasında Exchange içeriğinin yavaş araması, SharePoint veya OneDrive belge kitaplıklarıyla etkileşim kurarken yüksek aktarım süreleri ya da Microsoft Teams'da arama veya toplantı kalitesi düşük olabilir.

Bilgilendirilmiş ağ yönlendirmesi içindeki geri bildirim ve kurtarma mekanizması, bu tür sorunları neredeyse gerçek zamanlı olarak dinamik olarak algılamayı arar ve dağıtılan SD-WAN çözümünü otomatik kurtarma eylemleri gerçekleştirmesi için bilgilendirmektedir.

Veri paylaşım kanalı ayrıca SD-WAN çözümünden ağ düzeyinde optik verileri cihaz ve bağlı devrelerle ilişkili yapılandırma bilgileri ve kullanım istatistikleri de dahil olmak üzere düzenli aralıklarla almak için kullanılır. Hiçbir kişisel bilgi toplanmaz veya depolanmaz. Toplanan tüm bilgiler ofis konumlarına ve bağlı İnternet bağlantı hatlarına toplanır. Bu bilgiler, Microsoft'un Microsoft 365 hizmetleri ve uygulamaları kullanımınızla ilgili bildirilen sorunları daha verimli ve etkili bir şekilde çözmesine yardımcı olabilir.

>[!NOTE]
>Microsoft 365 bilgilendirilmiş ağ yönlendirmesi WW Ticari bulutundaki kiracıları destekler, ancak GCC Orta, GCC Yüksek, DoD, Almanya veya Çin bulutlarını desteklemez.

## <a name="requirements"></a>Gereksinimler

### <a name="integrated-sd-wan-solutions"></a>Tümleşik SD-WAN çözümleri

Microsoft, bilgilendirilmiş Microsoft 365 ağ yönlendirmesi ile tümleştirmeyi etkinleştirmek için çeşitli iş ortaklarıyla birlikte çalışmaktadır. Şu anda etkinleştirilmiş çözümler şunları içerir:

| Cihaz Oluşturucu | Çözüm Adı | En Düşük Sürüm |
| --- | --- | --- |
| Cisco | [IOS XE SD-WAN](https://go.microsoft.com/fwlink/?linkid=2151460) | 20.4/17.4 |

### <a name="network-topology"></a>Ağ topolojisi

Bilgilendirilmiş ağ yönlendirmesi şu anda belirli bir ofis konumu ve İnternet bağlantı hattıyla ilişkili trafiği, Microsoft'a ağ trafiği göndermek için kullanılan genel IP adresine göre tanımlar. 

Bir dal konumunda doğrudan İnternet erişimi sağlayan en az bir ağ bağlantı hattı olmaması durumunda, bilgilendirilmiş ağ yönlendirmesi önemli bir değer sağlamayabilir.

### <a name="application-usage"></a>Uygulama kullanımı

Uygulama deneyimi verileri (ağ kalitesi ölçümleri aracılığıyla yansıtılır) belirli Microsoft istemci uygulamalarının kullanımı aracılığıyla toplanır. Exchange ölçümler, Outlook istemcisinin kullanımını ve bazı Outlook Web App kullanımını yansıtır. SharePoint ve OneDrive ölçümleri, istemci uygulamasına bakılmaksızın kiracıya özgü SharePoint uç noktalarının kullanımını yansıtır. Teams ölçümler, Teams masaüstü istemcisinin kullanımını yansıtır. Ağ bağlantı hattının sistem durumu değerlendirilirken diğer uygulama trafiği dikkate alınmaz.

## <a name="enabling-informed-network-routing"></a>Bilinçli ağ yönlendirmeyi etkinleştirme

Bilgilendirilmiş ağ yönlendirmesini etkinleştirmek için birden çok adım gerekir ve bunların bir kısmının SD-WAN çözümünüzün yapılandırma arabiriminde gerçekleştirilmesi gerekir. Microsoft 365 yönetim merkezi yapılandırmaya devam etmeden önce SD-WAN çözümünde bilinçli ağ yönlendirmeyi etkinleştirme işlemini başlatma konusunda rehberlik için SD-WAN çözüm satıcınıza başvurun.

Microsoft 365 yönetim merkezi bilgilendirilmiş ağ yönlendirmeyi etkinleştirmeye hazır olduğunuzda, gerekli **Kullanıcı Yöneticisi** veya **Genel yönetici** izinlerine sahip olduğunuzdan emin olun.

>[!IMPORTANT]
>Seçilen SD-WAN çözümünün bilgilendirilmiş ağ yönlendirme veri paylaşım kanalına erişmesi için gerekli kiracı düzeyinde uygulama izinleri onayı sağlamak için, genel yönetici olarak aşağıdaki adımları gerçekleştirmeniz gerekir.


### <a name="step-1-open-sd-wan-solution-configuration-options"></a>1. Adım: SD-WAN çözümü yapılandırma seçeneklerini açma

[Microsoft 365 yönetim merkezi](https://admin.microsoft.com/) sol gezinti bölmesinde **Sistem Durumu > Ağ bağlantısı'nı** seçin.

Yönetim merkezinin bu bölümü, kuruluşunuz için toplu ağ bağlantısı ölçümleri ve bağlantınızı geliştirme yönergeleri sağlar. Yönetim merkezinde bulunan bu özellikler hakkında ek bilgi için [bkz. Microsoft 365 Yönetici Merkezi'nde ağ bağlantısı](office-365-network-mac-perf-overview.md).

Bilgilendirilmiş ağ yönlendirme yapılandırma bölmesini açmak için **Ayarlar > SD-WAN çözümünü** seçin. **Ayarlar** altında görünen diğer seçenekler yönetim merkezindeki genel ağ bağlantısı kılavuzu için geçerlidir ve bilgilendirilmiş ağ yönlendirmesini etkinleştirmek için gerekli değildir.

Yapılandırma bölmesinde **SD-WAN çözümünüzü ekle'yi** seçin.

### <a name="step-2-select-your-sd-wan-solution-and-data-storage-location"></a>2. Adım: SD-WAN çözümünüzü ve veri depolama konumunuzu seçin

Açılan kutularda, dağıttığınız SD-WAN çözümünü ve verilerin bilgilendirilmiş ağ yönlendirmesiyle ilişkili olmasını istediğiniz konumu seçin. Ek bilgi için [veri depolama](#data-storage) bölümüne bakın.

**İleri**'yi seçin.

### <a name="step-3-accept-terms-for-sharing-of-data"></a>3. Adım: Veri paylaşımı koşullarını kabul etme

Microsoft ile seçtiğiniz SD-WAN çözümü arasında veri paylaşımıyla ilgili sağlanan koşulları dikkatle okuyun ve onaylayın ve ardından belirtilen onay kutusunu seçin.

**İleri**'yi seçin.

### <a name="step-4-grant-permissions-to-the-sd-wan-solution"></a>4. Adım: SD-WAN çözümüne izin verme

Bu adım, Azure Active Directory (Azure AD) ile bir izin verme isteği başlatır. Seçtiğiniz SD-WAN çözümüne, bilgilendirilmiş ağ yönlendirme veri depolama alanına ve kiracınızla ilişkili hizmet durumu bilgilerine erişim izni veren kiracı düzeyinde izinler vermeniz istenir. Bu eylem **, Azure AD DC yöneticisi** veya **Genel yönetici** rolü izinleri gerektirir.

**Bu uygulamaya izin ver** bağlantısını seçin ve Azure AD isteklerini izleyin.

İzin verme işlemini tamamladıktan sonra **İleri'yi** seçin.

### <a name="step-5-confirm-your-configuration-settings"></a>5. Adım: Yapılandırma ayarlarınızı onaylayın

Kiracınız için bilinçli ağ yönlendirmesini etkinleştirmenin son adımı, sağladığınız ayarları görüntüleyen bir onay sayfasıdır. 

Kiracınız için artık bilinçli ağ yönlendirme etkinleştirildi.

**Bitti'yi** seçin ve ardından SD-WAN çözümü yapılandırma bölmesini kapatın.

## <a name="configuring-informed-network-routing"></a>Bilinçli ağ yönlendirmesini yapılandırma

SD-WAN çözümünüzde trafiğinizin normal koşullarda nasıl yönlendirileceği ve sorunlar algılanırsa kullanılması gereken alternatif yolları yapılandırma gibi, bilinçli ağ yönlendirme için yapılandırmanın büyük bölümünü gerçekleştireceksiniz. Bu yapılandırma adımlarıyla ilgili ayrıntılar için SD-WAN çözüm sağlayıcınıza başvurun.

Bilgilendirilmiş ağ yönlendirmesinin bu konumlara bağlantı sağlayan ağ bağlantı hatları ile ilişkili trafiği düzgün bir şekilde tanımlayabilmesi için her ofis konumunun Microsoft 365 yönetim merkezi yapılandırılması gerekir.

Office konumlar, Microsoft'un devam eden ağ telemetrisi koleksiyonunun bir parçası olarak otomatik olarak algılanabilir. Sonuç olarak, kiracınızın yönetim merkezinde bazı konumlar önceden doldurulmuş olabilir. 

Bu konumlar doğruysa, istenen her konum için bilgilendirilmiş ağ yönlendirme özelliğini etkinleştirmeniz ve İnternet bağlantı hatlarını ve bunların genel IP adreslerini yapılandırmanız yeterlidir. 

Otomatik olarak algılanan konumlar doğru değilse veya kiracınızda önceden doldurulmuş konum yoksa, kuruluşunuzun doğru topolojisini yansıtmak için konumları el ile eklemeniz veya düzenlemeniz gerekir.

### <a name="updating-locations"></a>Konumları güncelleştirme

Kiracınızın konumları **Konumlar** sekmesinde bulunabilir. Konumlar doğrudan listede düzenlenebilir veya CSV dosyası kullanılarak güncelleştirilebilir.

Bilgilendirilmiş ağ yönlendirmesini etkinleştirmek istediğiniz her ofis konumunun bu listede olduğundan emin olun.

>[!NOTE]
>Toplanan örnekler ve değerlendirmeyle ilgili diğer bilgiler için **Konumlar** listesindeki sütunlar, bilgilendirilmiş ağ yönlendirme özelliğiyle ilgili değildir.

### <a name="enabling-a-location-for-informed-network-routing"></a>Bilgilendirilmiş ağ yönlendirmesi için bir konumu etkinleştirme

1. **Konumlar** listesinde, hızlı eylemler menüsünde **Düzenle'yi** seçerek konum yapılandırma bölmesini açın.

2. **Bu konumda bilgilendirilmiş Microsoft 365 ağ yönlendirme kullan'ı** seçin.

3. Bu ofis konumu bölümündeki **Egress IP Adresi aralıklarına** bu ofis konumuna İnternet bağlantısı sağlayan tüm ağ bağlantı hatlarını ekleyin. Her bağlantı hattının ağ trafiğinizi temsil eden benzersiz genel IP adresi alt ağlarıyla ilişkilendirildiğinden emin olun.

4. Değişikliklerinizi kaydetmek için **Kaydet'i** seçin.

## <a name="disabling-informed-network-routing"></a>Bilgilendirilmiş ağ yönlendirmesini devre dışı bırakma

Bilgilendirilen ağ yönlendirme özelliği, SD-WAN çözüm ayarlarınızı sıfırlayarak kiracının tamamı için devre dışı bırakılabilir. Bu işlem Microsoft 365 içindeki tüm veri işlemeyi durdurur ancak yönetim merkezinde bilgilendirilmiş ağ yönlendirmesini de devre dışı bırakmanız gerekir.

### <a name="step-1-open-sd-wan-solution-configuration-options"></a>1. Adım: SD-WAN çözümü yapılandırma seçeneklerini açma

[Microsoft 365 yönetim merkezi](https://admin.microsoft.com/) sol gezinti bölmesinde **Sistem Durumu > Ağ bağlantısı'nı** seçin.

Bilgilendirilmiş ağ yönlendirme yapılandırma bölmesini açmak için **Ayarlar > SD-WAN çözümünü** seçin.

Yapılandırma bölmesi, şu anda yapılandırılmış olan SD-WAN çözümünüzün özetini gösterir.

### <a name="step-2-reset-your-configuration"></a>2. Adım: Yapılandırmanızı sıfırlama

Yapılandırma bölmesinde **SD-WAN çözüm ayarlarınızı sıfırla'yı** seçin.

Ayarlarınız sıfırlandı ve ağ yönlendirmesi devre dışı bırakıldı. [Bilgilendirilmiş ağ yönlendirmesini etkinleştirme'deki](#enabling-informed-network-routing) adımları izleyerek istediğiniz zaman yeniden etkinleştirebilirsiniz.

## <a name="data-storage"></a>Veri depolama

Microsoft ile SD-WAN çözüm sağlayıcısı arasında değiştirilen veriler, bilgilendirilmiş ağ yönlendirmesinin ilk etkinleştirilmesi sırasında seçilen veri depolama konumunda depolanır. Veri depolama konumu seçenekleri, verilerin depolandığı Microsoft Azure bölgeleri içeren coğrafi alanları temsil eder.

Veriler bu konumda 30 güne kadar saklanır. Devre dışı bırakıldığında, kalan tüm veriler bu 30 günlük saklama penceresinde kaldırılır.

Bu konumdaki veriler seçili SD-WAN çözümüyle değiştirilir ve yapılandırılan SD-WAN çözümünün konumu aynı bölgede olmayabilir. Müşteriler, üretim dağıtımından önce veri depolama konumu gereksinimlerini değerlendirmek için SD-WAN çözüm sağlayıcılarıyla birlikte çalışmalıdır.

## <a name="related-topics"></a>İlgili konular

[Microsoft 365 yönetim merkezi ağ bağlantısı](office-365-network-mac-perf-overview.md)

[ağ bağlantısı konum hizmetlerini Microsoft 365](office-365-network-mac-location-services.md)
