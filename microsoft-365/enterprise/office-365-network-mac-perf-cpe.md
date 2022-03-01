---
title: Microsoft 365 ağ yönlendirmesi
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
description: Microsoft 365 ağ yönlendirmesi
ms.openlocfilehash: f35257520385f8d4287c9a0839cd1e4e0e6b0aa3
ms.sourcegitcommit: 388279e10a160b85b345a8ad760f6816dda4e2ad
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2021
ms.locfileid: "62996618"
---
# <a name="microsoft-365-informed-network-routing"></a>Microsoft 365 ağ yönlendirmesi

Bilgiye bağlı ağ yönlendirme, Microsoft hizmeti uç noktalarıyla ağ bağlantınızı iyileştirmek ve geliştirmek için çeşitli Microsoft 365 uygulamalarını üçüncü taraf yazılım tanımlı ağ (SD-WAN) çözümleriyle tümleştiren bir özelliktir. İyileştirilmiş SD-WAN bağlantısı, geliştirilmiş kullanıcı deneyimleri ve performansına neden olabilir.

## <a name="overview"></a>Genel bakış

Bilgili ağ yönlendirmesi, Microsoft ile SD-WAN çözümünüz arasında iki yönlü bir veri paylaşım kanalı sağlar. Yapılandırılan her ofis konumu ve İnternet devresi için, Microsoft belirli İnternet devreleriyle ilişkilendirilmiş ağ trafiğine yönelik seçili Microsoft 365 uygulama deneyimlerinin kalitesiyle ilgili geri bildirimleri düzenli olarak SD-WAN çözümüyle paylaştır. SD-WAN çözümü, bu geri bildirimi kullanarak alternatif kullanılabilir bağlantılar aracılığıyla uygulama Microsoft 365 yönlendirerek akıllı kurtarma eylemleri gerçekleştirebilir. 

Gecikme süresi veya yüksek paket kaybı gibi belirli bir İnternet devresi yolunda hizmet performansı düşüşü sürekli algılamak zordur. Bu düşüşler, Exchange Online, SharePoint, OneDrive ve diğer uygulamalara Microsoft Teams. Yaygın belirtiler arasında içerikte yavaş Exchange, SharePoint veya OneDrive belge kitaplıklarıyla etkileşim kuruluyken yüksek aktarım süreleri ya da Microsoft Teams'te düşük arama veya toplantı kalitesi.

Bilgili ağ yönlendirme içindeki geri bildirim ve kurtarma mekanizması, bu tür sorunları gerçek zamanlı olarak dinamik olarak algıla karşılar ve dağıtılan SD-WAN çözümünü otomatik kurtarma eylemleri gerçekleştirerek bilgi verir.

Veri paylaşım kanalı, cihaz ve ekli devrelerle ilişkilendirilmiş yapılandırma bilgileri ve kullanım istatistikleri dahil olmak üzere SD-WAN çözümünden düzenli aralıklarla ağ düzeyinde optik veriler almak için de kullanılır. Hiçbir kişisel bilgi toplanmaz veya depolanabilir. Toplanan tüm bilgiler ofis konumlarında ve bağlı İnternet devreleri arasında toplanır. Bu bilgiler Microsoft'un hizmet ve uygulamaları kullanımınıza ilişkin bildirilen sorunları daha etkili ve etkili bir Microsoft 365 yardımcı olabilir.

>[!NOTE]
>Microsoft 365 bilgili ağ yönlendirmesi WW Ticari bulutlarında kiracıları destekler, ancak GCC Orta, GCC Yüksek, DoD, Almanya veya Çin bulutları için desteklemez.

## <a name="requirements"></a>Gereksinimler

### <a name="integrated-sd-wan-solutions"></a>Tümleşik SD-WAN çözümleri

Microsoft, bu ağ yönlendirmesi hakkında bilgi sahibi bir şekilde Microsoft 365 iş ortaklarıyla birlikte çalışıyor. Şu anda etkin olan çözümler şunlardır:

| Device Maker | Çözüm Adı | Minimum Sürüm |
| --- | --- | --- |
| Cisco | [IOS XE SD-WAN](https://go.microsoft.com/fwlink/?linkid=2151460) | 20.4/17.4 |

### <a name="network-topology"></a>Ağ topolojisi

Bilgiye dayalı ağ yönlendirme şu anda Microsoft'a ağ trafiğini gönderirken kullanılan genel IP adresine bağlı olarak belirli bir ofis konumu ve İnternet devresi ile ilişkilendirilmiş trafiği tanımlar. 

Bir şubede doğrudan İnternet erişimi sağlayan en az bir ağ devresi olmadığınız durumda, bilgiye bağlı ağ yönlendirmesi önemli bir değer sağlamayabilirsiniz.

### <a name="application-usage"></a>Uygulama kullanımı

Uygulama deneyimi verileri (ağ kalitesi ölçümleri aracılığıyla yansıtıldı) belirli Microsoft istemci uygulamaları aracılığıyla toplanır. Exchange ölçümler hem müşteri Outlook hem de kaynak kullanımı Outlook Web App gösterir. SharePoint ve OneDrive ölçümleri, istemci uygulaması ne olursa olsun kiracıya özgü SharePoint uç noktalarının kullanımını yansıtacaktır. Teams ölçümleri Teams masaüstü istemcisinin kullanımını yansıttır. Ağ devresi durumu değerlendir edilirken diğer uygulama trafiği dikkate alınmaz.

## <a name="enabling-informed-network-routing"></a>Bilgili ağ yönlendirmesini etkinleştirme

Bilgiye bağlı ağ yönlendirmesini etkinleştirmek için birden çok adım gerekir ve bunlardan bazılarının SD-WAN çözümünün yapılandırma arabirimi içinde gerçekleştirılması gerekir. Yapılandırmaya devam etmeden önce, SD-WAN çözümünde bilinçli bir ağ yönlendirmesini etkinleştirme işlemini başlatma konusunda yol gösterici bilgi için SD-WAN çözüm satıcınıza Microsoft 365 yönetim merkezi.

Ağ sayfasında bilinçli ağ yönlendirmeyi etkinleştirmeye hazır Microsoft 365 yönetim merkezi, gerekli Kullanıcı Yöneticisi veya Genel **yönetici** izinlerine sahip **olduğunuzdan emin** olun.

>[!IMPORTANT]
>Bilgili ağ yönlendirme veri paylaşım kanalına erişmek üzere seçili SD-WAN çözümü için gerekli kiracı düzeyinde uygulama izinleri izni sağlamak için genel yönetici olarak aşağıdaki adımları gerçekleştirmeniz gerekir.


### <a name="step-1-open-sd-wan-solution-configuration-options"></a>1. Adım: SD-WAN çözümü yapılandırma seçeneklerini açma

Gezinti [Microsoft 365 yönetim merkezi](https://admin.microsoft.com/) gezinti **bölmesinde Durum > Ağ** bağlantısı'ni seçin.

Yönetim merkezinin bu bölümünde, organizasyonunız için toplanan ağ bağlantısı ölçümleri ve bağlantınızı iyileştirmeyle ilgili kılavuz bilgiler yer almaktadır. Yönetim [merkezinde bulunan bu özellikler hakkında ek bilgi Microsoft 365 Yönetici](office-365-network-mac-perf-overview.md) için bkz. Yönetim Merkezi'nde ağ bağlantısı.

Bilgi **Ayarlar > ağ yönlendirme yapılandırma bölmesini açmak için SD-WAN** çözümünü kullanın. Bu iletişim kutusunda görünen **diğer Ayarlar** yönetim merkezinde bulunan genel ağ bağlantısı kılavuzu için geçerlidir ve bilgili ağ yönlendirmeyi etkinleştirmek için gerekli değildir.

Yapılandırma bölmesinde **SD-WAN çözümlerinizi ekleyin'i seçin**.

### <a name="step-2-select-your-sd-wan-solution-and-data-storage-location"></a>2. Adım: SD-WAN çözüm ve veri depolama konumu seçin

Açılan kutularda, dağıtılan SD-WAN çözümünü ve bilgili ağ yönlendirmesi ile ilişkili verilerin depolandığı konumu seçin. Ek bilgi [için veri](#data-storage) depolama bölümüne bakın.

**İleri**'yi seçin.

### <a name="step-3-accept-terms-for-sharing-of-data"></a>3. Adım: Veri paylaşımı koşullarını kabul etme

Microsoft ile seçtiğiniz SD-WAN çözümü arasında veri paylaşımıyla ilgili sağlanan koşulları dikkatle okuyun ve kabul edin ve ardından gösterilen onay kutusunu seçin.

**İleri**'yi seçin.

### <a name="step-4-grant-permissions-to-the-sd-wan-solution"></a>4. Adım: SD-WAN çözümüne izin verin

Bu adım, izin atama isteğini Azure Active Directory (Azure AD) olarak başlatacak. Seçtiğiniz SD-WAN çözümüne, bilgiye sahip ağ yönlendirme veri depolaması ve kiracınız ile ilişkili hizmet durumu bilgilerine erişim izni vermek için kiracı düzeyinde izinler vermeniz willten. Bu eylem **için Azure AD DC yöneticisi veya** **Genel yönetici rolü** izinleri gerekir.

Bu uygulama **için izin ver bağlantısını** seçin ve Azure AD isteklerini izleyin.

Verilen izinleri tamamlandıktan sonra, Sonraki'yi **seçin**.

### <a name="step-5-confirm-your-configuration-settings"></a>5. Adım: Yapılandırma ayarlarınızı onaylama

Kiracınız için bilinçli ağ yönlendirmesini etkinleştirmenin son adımı, sağlanıyor olan ayarları görüntüleyen bir onay sayfasıdır. 

Kiracınız için artık bilgili ağ yönlendirme etkinleştirilmiştir.

**Bitti'yi** seçin ve ardından SD-WAN çözümü yapılandırma bölmesini kapatın.

## <a name="configuring-informed-network-routing"></a>Bilgiye bağlı ağ yönlendirmeyi yapılandırma

SD-WAN çözümünüz içinde bilinçli ağ yönlendirmesi için yapılandırmanın büyük bir işlemini gerçekleştirebilirsiniz; örneğin, normal koşullarda trafiğinizin nasıl yönlendirneceklerini yapılandırma ve sorunlar algılandığında kullanılacak alternatif yollar. Bu yapılandırma adımlarıyla ilgili ayrıntılar için SD-WAN çözüm sağlayıcınıza başvurun.

Bilgiye bağlı ağ yönlendirmenin bu konumlara bağlantı sağlayan ağ devreleriyle ilişkilendirilmiş trafiği düzgün tanımlay uygulamasını sağlamak için, her ofis konumu Microsoft 365 yönetim merkezi yapılandırılması gerekir.

Office, Microsoft'un devam eden ağ telemetrisi koleksiyonu kapsamında otomatik olarak algılanmış olabilir. Sonuç olarak, kiracınız için yönetim merkezinde bazı konumlar önceden doldurulmuş olabilir. 

Bu konumlar doğru ise, istenen her konum için bilinçli ağ yönlendirme özelliğini etkinleştirmeniz ve İnternet devrelerini ve bunların genel IP adreslerini yapılandırmanız gerekir. 

Otomatik olarak algılanan konumlar doğru yoksa veya kiracınız içinde önceden doldurulmuş bir konum yoksa, konumlar, kuruma uygun bir topolojiyi yansıtmak için el ile eklemeniz veya düzenlemeniz gerekir.

### <a name="updating-locations"></a>Konumları güncelleştirme

Kiracınız için konumlar, Konumlar **sekmesinin altında** bulunabilir. Konumlar doğrudan listede düzenlenebilir veya CSV dosyası kullanılarak güncelleştirilebilir.

Bu listede, bilgiye bağlı ağ yönlendirmeyi etkinleştirmek istediğiniz her ofis konumunun mevcut olduğundan emin olun.

>[!NOTE]
>Konumlar listesinde **toplanan örneklere** ilişkin sütunlar ve değerlendirmeyle ilgili diğer bilgiler, bilgiye sahip ağ yönlendirme özelliğiyle ilgili değildir.

### <a name="enabling-a-location-for-informed-network-routing"></a>Bilgiye bağlı ağ yönlendirmesi için bir konumu etkinleştirme

1. Konumlar **listesinde,** hızlı eylemler **menüsünden** Düzenle'yi seçerek konum yapılandırma bölmesini açın.

2. Bu **konumda Microsoft 365 ağ yönlendirmesi kullan'ı seçin**.

3. Bu ofis konumu bölümündeki IP Adresi aralıklarında, bu ofis **Egress İnternet bağlantısı sağlayan tüm ağ devrelerini** ekleyin. Her devrenin, ağ trafiğinizi temsil eden benzersiz genel IP adresi alt ağlarıyla ilişkilendirilmiş olduğundan emin olun.

4. **Değişikliklerinizi kaydetmek** için Kaydet'i seçin.

## <a name="disabling-informed-network-routing"></a>Bilgili ağ yönlendirmesini devre dışı bırakma

SD-WAN çözümü ayarlarınızı sıfırlayarak, bilgiye sahip ağ yönlendirme özelliği kiracının tamamı için devre dışı bırakılabilir. Bu işlem tüm verinin yönetim merkezinden Microsoft 365 durdursa da, yönetim merkezi içinde bilgili ağ yönlendirmeyi devre dışı bırakmanız gerekir.

### <a name="step-1-open-sd-wan-solution-configuration-options"></a>1. Adım: SD-WAN çözümü yapılandırma seçeneklerini açma

Gezinti [Microsoft 365 yönetim merkezi](https://admin.microsoft.com/) gezinti **bölmesinde > Durum** Bilgi Sistemi Bağlantısı'ni seçin.

Bilgi **Ayarlar > ağ yönlendirme yapılandırma bölmesini açmak için SD-WAN** çözümünü kullanın.

Yapılandırma bölmesinde, yapılandırılmış durumdaki SD-WAN çözümünüz özet gösterilir.

### <a name="step-2-reset-your-configuration"></a>2. Adım: Yapılandırmanızı sıfırlama

Yapılandırma bölmesinde **SD-WAN çözüm ayarlarınızı sıfırla'yı seçin**.

Ayarlarınız artık sıfırlandı ve bilgiye bağlı ağ yönlendirmesi devre dışı bırakıldı. Bilgili ağ yönlendirmesini etkinleştirme'nin adımlarına bakarak bunu [her zaman yeniden etkinleştirebilirsiniz](#enabling-informed-network-routing).

## <a name="data-storage"></a>Veri depolama

Microsoft ile SD-WAN çözüm sağlayıcısı arasında veri alışverişi yapılan veriler, bilgili ağ yönlendirmenin ilk etkinleştirmesi sırasında seçilen veri depolama konumda depolanır. Veri depolama konumu seçenekleri, verilerin depolandığı Microsoft Azure coğrafi alanları temsil ediyor.

Veriler 30 gün boyunca bu konumda korunur. Devre dışı bırakıldığı zaman, bu 30 günlük bekletme penceresinde kalan tüm veriler kaldırılır.

Bu konumdaki veriler seçili SD-WAN çözümüyle takas edildi ve yapılandırılmış SD-WAN çözümünün konumu aynı bölgede yer alamıyor olabilir. Müşterilerin üretim dağıtımı öncesinde veri depolama konumu gereksinimlerini değerlendirmek için SD-WAN çözüm sağlayıcılarıyla birlikte çalışmaları gerekir.

## <a name="related-topics"></a>İlgili konular

[Ağ bağlantısı Microsoft 365 yönetim merkezi](office-365-network-mac-perf-overview.md)

[Microsoft 365 Bağlantısı Konum Hizmetleri'ne Bağlan'a](office-365-network-mac-location-services.md)
