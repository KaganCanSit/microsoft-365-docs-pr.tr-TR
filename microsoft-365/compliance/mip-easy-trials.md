---
title: E-posta etiketlerinin varsayılan etiketlerini ve Microsoft Bilgi Koruması
f1.keywords:
- CSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
description: Hassas içeriği sınıflandırmak ve korumak için Microsoft Bilgi Koruması (MIP) etiketleri ve ilkeleri hakkında bilgi edinebilirsiniz.
ms.openlocfilehash: a0634a8f67e28d84334cfadd4be7d9694084af6c
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63032471"
---
# <a name="default-labels-and-policies-for-microsoft-information-protection"></a>Posta için varsayılan etiketler ve Microsoft Bilgi Koruması

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Uygun müşteriler, E-posta (MIP) için varsayılan Microsoft Bilgi Koruması ve ilkelerini etkinleştir olabilir: 

- Duyarlılık etiketleri ve duyarlılık etiketi ilkesi
- İstemci tarafı otomatik etiketleme
- Hizmet tarafı otomatik etiketleme
- Verileri ve cihazlarınız için veri kaybı önleme (DLP) Teams ilkeleri

Bu varsayılan yapılandırmalar, Uyumluluk Ayarları'Microsoft Bilgi Koruması hızlı Microsoft 365 yardımcı olur. Bunları olduğu gibi kullanabilir, yalnızca birkaç değişiklik yapabilirsiniz veya iş gereksinimlerinize daha iyi uyacak şekilde tümüyle özelleştirebilirsiniz. 

Uygunluk, Uyumluluk Uyumluluğu için [ücretsiz deneme Microsoft 365 müşterileri](compliance-easy-trials.md) ve zaten bir yasal planı olan bazı Microsoft 365 E5 içerir:

- **Yeni müşteriler**: Uyumluluk uyumluluk Microsoft 365 30 gündür yoksa, kiracınız listelenen tüm varsayılan yapılandırmaları etkinleştirebilirsiniz. Bunları istediğiniz zaman devre dışı bırakamaz, kaldırabilir veya düzenleyebilirsiniz.

- **Mevcut müşteriler**: Uyumluluk uyumluluk Microsoft 365 30 gündür yoksa, eşdeğerini henüz yapılandırmadınız varsayılan yapılandırmaları etkinleştirebilirsiniz:

    | Varsayılan yapılandırma| Eşdeğer |
    |:-----|:-----|
    |Duyarlılık etiketleri ve duyarlılık etiketi ilkesi | Yayımlanmış duyarlılık etiketleri |
    |İstemci tarafı otomatik etiketleme | Kullanıcılara otomatik olarak uygulanacak (veya kullanıcılara önerilecek) bir veya daha fazla duyarlılık Office.|
    |Hizmet tarafı otomatik etiketleme | En az bir açık otomatik etiket ilkesi|
    |DLP for Teams | En az bir DLP ilkesi Teams|
    |Cihazlar için DLP | Cihazlar için en az bir DLP ilkesi|

## <a name="activate-the-default-labels-and-policies"></a>Varsayılan etiketleri ve ilkeleri etkinleştirme

Bu önceden yapılandırılmış etiketleri ve ilkeleri almak için: 

1. Kayıttan [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com/) **SolutionsInformation** >  **protection'ı seçin**
    
    Bu seçeneği hemen görmüyorsanız, önce Gezinti bölmesinden **Hepsini göster'i** seçin. 
    
2. Varsayılan etiket ve ilkeleri Microsoft Bilgi Koruması için uygunsanız, aşağıdaki bilgileri görebilir ve burada varsayılan etiketleri ve ilkeleri etkinleştirebilirsiniz. Örneğin:
    
    :::image type="content" alt-text="Microsoft Bilgi Koruması yapılandırılmış etiketler ve ilkeler için etkinleştirmeyi tıklatın." source="../media/mip-preconfigured.png" lightbox="../media/mip-preconfigured.png":::
    
    Etkinleştirme seçeneğiyle birlikte bu bilgileri görmüyorsanız, şu anda otomatik duyarlılık etiketleri ve ilkeleri oluşturma için uygun değilseniz. Daha sonra bu durumun değişp değişmediğini görmek için yeniden denetlemeyi deneyebilir veya aynı etiketleri ve ilkeleri el ile oluşturmak için aşağıdaki ayarlar bilgilerini kullanabilirsiniz.

3. Artık daha fazla duyarlılık ve SharePoint duyarlılık OneDrive. Bu adım, Web için Office'de duyarlılık etiketlerini kullanmak için, SharePoint ve otomatik etiket ilkelerini kullanmak için OneDrive.
   
    Bilgi Korumasına Genel Bakış sekmesinin üst kısmında yer alan aşağıdaki başlığı **kullanın** ve Şimdi **aç'ı seçin**. Bu başlığı görmüyorsanız, kullanıcı etiketleri ve SharePoint OneDrive zaten etkinleştirilmiştir.
    
    ![Başlık ve başlık SharePoint duyarlılık OneDrive etkinleştirin.](../media/turn-on-mip-labels.png)
    
    Bu özellik hakkında daha fazla bilgi için bkz. Dosya ve [klasörlerin Office için duyarlılık SharePoint OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

## <a name="default-sensitivity-labels"></a>Varsayılan duyarlılık etiketleri

Yayımlanmış duyarlılık etiketleriniz olmadığınız zaman, sizin için aşağıdaki etiketleri oluşturuz:


|Etiket adı|Kullanıcılar için etiket açıklaması|Ayarlar|
|-------------------------------|---------------------------|-----------------|
|Personal|İşle ilgili olmayan veriler, yalnızca kişisel kullanım için.|**Kapsam**: Dosya, E-posta <br /><br />**İçerik işaretleme**: Hayır<br /><br />**Otomatik etiketleme**: Hayır <br /><br />**Grup ayarları**: Hayır<br /><br />**Site ayarları**: Hayır <br /><br />**Veritabanı sütunları için otomatik etiketleme**: Yok|
|Genel|Özel olarak hazırlanmış ve kamu kullanımı için onaylanmış iş verileri.|**Kapsam**: Dosya, E-posta <br /><br />**İçerik işaretleme**: Hayır<br /><br />**Otomatik etiketleme**: Hayır <br /><br />**Grup ayarları**: Hayır<br /><br />**Site ayarları**: Hayır <br /><br />**Veritabanı sütunları için otomatik etiketleme**: Yok|
|Genel|Kamu kullanımına yönelik değildir iş verileri. Bununla birlikte, gerektiğinde bunu dış iş ortaklarıyla paylaşabilirsiniz. Örnekler, şirket içi telefon dizininden, kuruluş şemalarından, şirket içi standartlarından ve şirket içi iletişimlerin çoğuna örnek olarak verilmiştir.|**Kapsam**: Dosya, E-posta <br /><br />**İçerik işaretleme**: Hayır<br /><br />**Otomatik etiketleme**: Hayır <br /><br />**Grup ayarları**: Hayır<br /><br />**Site ayarları**: Hayır <br /><br />**Veritabanı sütunları için otomatik etiketleme**: Yok|
|Genel <br /> \ Herkes (kısıtlanmamış)|Kamu kullanımına yönelik olmayan ancak uygun olduğunda dış iş ortaklarıyla paylaşılacak kuruluş verileri. Örnek olarak, hassas bilgiler veya yayınlanan pazarlama malzemelerinin yer içermesi yer alan müşteri konuşmaları örnek olarak verilmiştir.|**Kapsam**: Dosya, E-posta <br /><br />**İçerik işaretleme**: Hayır<br /><br />**Otomatik etiketleme**: Hayır <br /><br />**Grup ayarları**: Hayır<br /><br />**Site ayarları**: Hayır <br /><br />**Veritabanı sütunları için otomatik etiketleme**: Yok|
|Genel <br /> \ Tüm Çalışanlar (kısıtlanmamış)|Kamu kullanımına yönelik olmayan kuruluş verileri. Bu içeriği dış iş ortaklarıyla paylaşmanız gerekirse, diğer veri sahipleriyle paylaşmanın kabul olduğunu onaylayın ve etiketi Genel \ Herkes (kısıtlanmamış) olarak değiştirin. Örnekler, şirket içi telefon dizininden, kuruluş şemalarından, şirket içi standartlarından ve şirket içi iletişimlerin çoğuna örnek olarak verilmiştir.|**Kapsam**: Dosya, E-posta <br /><br />**İçerik işaretleme**: Hayır<br /><br />**Otomatik etiketleme**: Hayır <br /><br />**Grup ayarları**: Hayır<br /><br />**Site ayarları**: Hayır <br /><br />**Veritabanı sütunları için otomatik etiketleme**: Yok|
|Gizli|Yetkisiz kullanıcılarla paylaşılırsa işletmeye zarar verabilecek hassas iş verileri. Örnek olarak sözleşmeler, güvenlik raporları, tahmin özetleri ve satış hesabı verileri örnek olarak verilmiştir.|**Kapsam**: Dosya, E-posta <br /><br />**İçerik işaretleme**: Hayır<br /><br />**Otomatik etiketleme**: Hayır <br /><br />**Grup ayarları**: Hayır<br /><br />**Site ayarları**: Hayır <br /><br />**Veritabanı sütunları için otomatik etiketleme**: Yok|
|Gizli <br /> \ Herkes (kısıtlanmamış)|Şifrelenmeleri gerek olmayan gizli veriler. Bu seçeneği özenli ve uygun işletme gerekçeleriyle kullanın.|İstemci tarafı otomatik [etiketleme ve hizmet tarafındaki otomatik etiketleme](#client-side-auto-labeling) [için bu etiket seçilir](#service-side-auto-labeling).<br /><br /> **Kapsam**: Dosya, E-posta <br /><br />**İçerik işaretleme**: Alt Bilgi: Gizli olarak sınıflandırılmış<br /><br />**Otomatik etiketleme**: Kullanıcıların etiketi uygulamalarını önerin <br /><br />**Grup ayarları**: Hayır<br /><br />**Site ayarları**: Hayır <br /><br />**Veritabanı sütunları için otomatik etiketleme**: Yok|
|Gizli <br /> \ Tüm Çalışanlar|Tüm çalışanların tam izinlerine olanak sağlayan, koruma gerektiren gizli veriler. Veri sahipleri içeriği izleyebilir ve iptal ettirebilirsiniz.|İstemci tarafı otomatik [etiketleme ve hizmet tarafındaki otomatik etiketleme](#client-side-auto-labeling) [için bu etiket seçilir](#service-side-auto-labeling).<br /><br /> **Kapsam**: Dosya, E-posta <br /><br />**Şifreleme**: Kuruluşta tüm kullanıcılar ve gruplar: Co-Author<br /><br />**İçerik işaretleme**: Alt Bilgi: Gizli olarak sınıflandırılmış<br /><br />**Otomatik etiketleme**: Kullanıcıların etiketi uygulamalarını önerin <br /><br />**Grup ayarları**: Hayır<br /><br />**Site ayarları**: Hayır <br /><br />**Veritabanı sütunları için otomatik etiketleme**: Yok |
|Gizli <br /> \ Güvenilen Kişiler|Kuruluşun içindeki ve dışındaki güvenilir kişilerle paylaşılacak gizli veriler. Ayrıca bu kişiler gerektiğinde verileri yeniden paylaşabilirsiniz.|**Kapsam**: Dosya, E-posta <br /><br />**Şifreleme**: Kullanıcıların izin atamasına izin verin: <br /> - Encrypt-Only için Outlook <br />- Word, PowerPoint ve Excel'de kullanıcılara sor<br /><br />**İçerik işaretleme**: Alt Bilgi: Gizli olarak sınıflandırılmış<br /><br />**Otomatik etiketleme**: Hayır <br /><br />**Grup ayarları**: Hayır<br /><br />**Site ayarları**: Hayır <br /><br />**Veritabanı sütunları için otomatik etiketleme**: Yok|
|Çok Gizli|Yetkisiz kullanıcılarla paylaşılırsa işletmeye zarar verabilecek çok hassas iş verileri. Örnekler çalışan ve müşteri bilgileri, parolalar, kaynak kodu ve önceden duyurulan mali raporlardır.|**Kapsam**: Dosya, E-posta <br /><br />**İçerik işaretleme**: Filigran: ÇOK GİzLİ<br /><br />**Otomatik etiketleme**: Hayır <br /><br />**Grup ayarları**: Hayır<br /><br />**Site ayarları**: Hayır <br /><br />**Veritabanı sütunları için otomatik etiketleme**: Yok|
|Çok Gizli <br /> \ Tüm Çalışanlar|Tüm çalışanların bu içeriği görüntüleme, düzenleme ve yanıtlama izinlerini görüntülemelerine olanak sağlayan çok gizli veriler. Veri sahipleri içeriği izleyebilir ve iptal ettirebilirsiniz.|**Kapsam**: Dosya, E-posta <br /><br />**Şifreleme**: Kuruluşta tüm kullanıcılar ve gruplar: Co-Author<br /><br />**İçerik işaretleme**: Alt Bilgi: Çok Gizli Olarak Sınıflandırılır<br /><br />**Otomatik etiketleme**: Hayır <br /><br />**Grup ayarları**: Hayır<br /><br />**Site ayarları**: Hayır <br /><br />**Veritabanı sütunları için otomatik etiketleme**: Yok|
|Çok Gizli <br /> \ Belirli Kişiler |Koruma gerektiren çok gizli veriler, yalnızca sizin belirttiğiniz kişiler ve seçtiğiniz izin düzeyi ile  hangi düzeyde görüntülensin?|**Kapsam**: Dosya, E-posta <br /><br />**Şifreleme**: Kullanıcıların izin atamasına izin verin: <br />- E-posta için İleri'Outlook <br />- Word, PowerPoint ve Excel'de kullanıcılara sor<br /><br />**İçerik işaretleme**: Alt Bilgi: Çok Gizli Olarak Sınıflandırılır<br /><br />**Otomatik etiketleme**: Hayır <br /><br />**Grup ayarları**: Hayır<br /><br />**Site ayarları**: Hayır <br /><br />**Veritabanı sütunları için otomatik etiketleme**: Yok|

> [!NOTE]
> Etiket adları ve açıklamaları otomatik olarak aşağıdaki yerel olarak kullanılabilir: ABD İngilizcesi, Basitleştirilmiş Çince ve Geleneksel, Fransızca, Almanca, İtalyanca, Japonca, Kore dili, Portekizce Brezilya Portekizcesi, Rusça ve İspanyolca.
> 
> Başka diller de gerekirse, [PowerShell kullanarak çevirilerinizi belirtabilirsiniz](create-sensitivity-labels.md#example-configuration-to-configure-a-sensitivity-label-for-different-languages).

Bu yapılandırma ayarları ve duyarlılık etiketlerinin neler yapıları hakkında daha fazla bilgi için bkz[. Duyarlılık etiketlerinin neler yap?](sensitivity-labels.md#what-sensitivity-labels-can-do)

Bu varsayılan duyarlılık etiketlerini düzenlemeniz gerekirse bkz. [Duyarlılık etiketlerini oluşturma ve yapılandırma](create-sensitivity-labels.md#create-and-configure-sensitivity-labels).

## <a name="default-sensitivity-label-policy"></a>Varsayılan duyarlılık etiketi ilkesi

Varsayılan duyarlılık etiketi ilkesi, etiketlerin kullanıcıların belgelerini ve e-postalarını duyarlılık etiketleriyle etiketlemeye başlamalarını sağlar. Aşağıdaki yapılandırmaya sahip:

- Varsayılan etiketleri kiracılı tüm kullanıcılara yayımlama
- Etiketsiz belgeler **ve e-postalar** \  **için GeneralAll Employees (** kısıtlanmamış) varsayılan etiketi
- Kullanıcılar bir etiketi kaldırmak veya sınıflandırmasını düşürmek için gerekçe sağlamalı

Bu ilke ayarları ve kullanılabilir diğer ilke ayarları hakkında daha fazla bilgi için bkz [. Etiket ilkeleri neler yapar](sensitivity-labels.md#what-label-policies-can-do).

Bu varsayılan ilke ayarlarını düzenlemeniz gerekirse bkz. [Etiket ilkesi oluşturarak duyarlılık etiketlerini yayımlama](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy).

Bu etiketleri Windows, macOS, iOS ve Android üzerinde Office uygulamalarına kullanıyorsanız, kullanıcılar dört saat içinde yeni etiketleri görebilir ve siz tarayıcıyı yenilerken Word, Excel ve Web üzerinde PowerPoint için bir saat içinde yeni etiketler görebilir. Bununla birlikte, değişikliklerin tüm uygulama ve hizmetlere çoğaltılması için 24 saate kadar izin vermeniz gerekir.

## <a name="client-side-auto-labeling"></a>İstemci tarafı otomatik etiketleme

Varsayılan istemci tarafı otomatik etiketleme yapılandırması, birlikte çalıştığı belgelerde veya e-postalarda kredi kartı numaraları algılayana kadar kullanıcıların otomatik olarak bir duyarlılık etiketi uygulamalarını öneririz. Otomatik olarak uygulanmak yerine öneri olarak, bu yapılandırma içerikle ilgili vurgulamak için iyi bir ilk adım olarak hizmet ediyor ve kullanıcıları belgelerini ve e-postalarını etiketleme uygulamasına tanıtıyor.

İstemci tarafı otomatik etiketleme yalnızca Word, Excel, PowerPoint ve Office uygulamaları tarafından Office belgeler ve e-Outlook. 

Varsayılan istemci tarafı otomatik etiketleme, aşağıdaki yapılandırmaya sahip olur: 

- Bir belgede veya e-postada 1-9 durumda kredi kartı numarası bulunuyorsa, kullanıcının **ConfidentialAnyone** \  (kısıtlanmamış) duyarlılık etiketini **uygulamasini önerin** 

- Bir belge veya e-postada 10 veya daha fazla kredi kartı numarası örneği varsa, **kullanıcıya GizliTüm** \  Çalışanlar duyarlılık etiketini **uygulamalarını önerin** 

> [!NOTE]
> Kendi duyarlılık etiketlerinizin yayımlanmış olduğunu algıladık, sizden otomatik etiketleme için kendi etiketlerinizi seçmenizi ve bunu sizin için yapılandırmanızı istenir.

İstemci tarafı otomatik etiketleme yapılandırmasını düzenlemek için bkz. Birden çok uygulama için otomatik [etiketlemeyi Office.](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps)

## <a name="service-side-auto-labeling"></a>Hizmet tarafı otomatik etiketleme 

Hizmet tarafı otomatik etiketleme, kalan hassas belgeleri ve geçişte e-postaları etiketlemeye yardımcı olur. Varsayılan hizmet tarafı otomatik etiketleme ilkesi, tüm SharePoint veya OneDrive sitelerinde depolanan belgeler ve posta yoluyla gönderilen tüm e-postalar için benzetim modunda bir ilke Exchange Online. Benzetim modunda, öğeler aslında ilkeyi açıncaya kadar etiketli değildir. Benzetim modu, ilke açıkken hangi öğelerin etiket olacağını önizlemenize olanak sağlar, bu nedenle asıl etiketleme için ilkeyi kiracınıza dağıtmadan önce etiketleme özelliğine güvenebilirsiniz. 

Varsayılan hizmet tarafı otomatik etiketleme, aşağıdaki yapılandırmaya sahip olur: 

- Belgede 1-9 arasında kredi kartı numarası örneği varsa **ConfidentialAnyone**  \  (sınırsız) duyarlılık etiketini kullanın

- Bir belge veya e-postada 10 veya daha fazla kredi kartı numarası örneği varsa, **kullanıcıya GizliTüm** \  Çalışanlar duyarlılık etiketini **uygulamalarını önerin** 

> [!NOTE]
> Kendi duyarlılık etiketlerinizin yayımlanmış olduğunu belirlediyseniz, otomatik etiket ilkeniz için kendi etiketlerinizi seçmeniz istenir.

Benzetim tamamlandığında, sonuçları gözden geçirin ve onlardan memnunsanız ilkeyi aç'

Benzetim modu hakkında daha fazla bilgi için bkz[. Benzetim modu hakkında bilgi.](apply-sensitivity-label-automatically.md#learn-about-simulation-mode)

Hizmet tarafı otomatik etiketleme ilkesi düzenlemek için bkz. SharePoint, OneDrive ve Exchange için otomatik etiket [ilkelerini yapılandırma](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange).

## <a name="dlp-for-teams"></a>DLP for Teams

Varsayılan DLP ilkesi, Teams sohbetler ve kanal mesajlarında kredi Teams numaralarının varlığını algılar. Bu hassas bilgiler algılandığında, yöneticiler düşük önem düzeyi uyarısı bildirimi alır.

Bu ilke, ilke ipucu görünür veya engellenmiş ileti olmayan kullanıcılar için çalışmaz, ancak yöneticilerin bu iletilerde paylaşılan hassas bilgilerin kayıtları olur. Gerekirse, bu varsayılan yapılandırmayı değiştirmek için ayarları düzenleyebilirsiniz.

Bu ilkenin sonuçlarını görmek için [DLP Etkinlik Gezgini'ni kullanın](dlp-learn-about-dlp.md#dlp-activity-explorer).

DLP ilkesi düzenlemek için bkz. [DLP ilkesi oluşturma, sınama ve ayarlama](create-test-tune-dlp-policy.md).

## <a name="dlp-for-devices"></a>Cihazlar için DLP

Cihazlar için varsayılan DLP ilkesi, mobil cihazlarda kredi kartı numaraları olduğunu ve bu numaralara uyumluluk Windows 10 Microsoft 365 olduğunu algılar. Daha sonra aşağıdaki eylemleri denetimler (engellemez): 

- Upload izin verilmeyen tarayıcılar tarafından bulut hizmeti etki alanlarına veya erişime erişme

- Panoya, USB'ye veya ağ paylaşımına kopyalama 

- Izin verilmeyen uygulamalara göre erişim 

- Yazdır 

- Aynı uygulamada izin verilmeyen dosyaları kullanarak kopyalama Bluetooth taşıma 

- Uzak masaüstü hizmetleri 

İçerikte 10 veya daha fazla kredi kartı örneği ve listelenen etkinliklerden biri veya daha fazlası algılanırsa, yöneticilere orta önem düzeyine sahip bir uyarı bildirimi gönderilir.

Bu ilke, ilke ipucu görünür veya hiçbir eylem engeli olmayan kullanıcılar için engellemez, ancak yöneticilerin tüm şüpheli etkinliklerin kayıtları olur. Gerekirse, bu varsayılan yapılandırmayı değiştirmek için bu ayarları düzenleyebilirsiniz.

Bu ilkenin sonuçlarını görmek için [DLP Etkinlik Gezgini'ni kullanın](dlp-learn-about-dlp.md#dlp-activity-explorer).

DLP ilkesi düzenlemek için bkz. [DLP ilkesi oluşturma, sınama ve ayarlama](create-test-tune-dlp-policy.md).

## <a name="additional-resources"></a>Ek kaynaklar

Duyarlılık etiketleri, veri kaybını önleme ve bu etiketlerle kullanılabilen tüm özellikler hakkında daha fazla bilgi Microsoft Bilgi Koruması aşağıdaki kaynaklara bakın:

- [Duyarlılık etiketleri hakkında bilgi edinin](sensitivity-labels.md)
- [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md)
- [Microsoft Bilgi Koruması'da Microsoft 365](information-protection.md)
