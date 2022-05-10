---
title: Verilerinizi korumak için varsayılan etiketler ve ilkeler hakkında bilgi edinin
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
description: Hassas içeriği sınıflandırmak ve korumak için Microsoft Purview Information Protection için varsayılan etiketler ve ilkeler hakkında bilgi edinin.
ms.openlocfilehash: 486286780eaa3a2deedb2c3df837a93814280f39
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/09/2022
ms.locfileid: "65286460"
---
# <a name="default-labels-and-policies-to-protect-your-data"></a>Verilerinizi korumak için varsayılan etiketler ve politikalar

>*[Güvenlik & uyumluluğu için lisanslama yönergelerini Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Uygun müşteriler Microsoft Purview Information Protection için varsayılan etiketleri ve ilkeleri etkinleştirebilir: 

- Duyarlılık etiketleri ve duyarlılık etiketi ilkesi
- İstemci tarafı otomatik etiketleme
- Hizmet tarafı otomatik etiketleme
- Teams ve cihazlar için veri kaybı önleme (DLP) ilkeleri

Bu varsayılan yapılandırmalar, Microsoft 365 için Microsoft Purview Information Protection ile hızlı bir şekilde çalışmaya başlamanıza yardımcı olur. Bunları olduğu gibi kullanabilir, yalnızca birkaç değişiklik yapabilir veya iş gereksinimlerinize daha iyi uyacak şekilde tamamen özelleştirebilirsiniz. 

Uygunluk, [Microsoft Purview için ücretsiz deneme sürümü](compliance-easy-trials.md) olan müşterileri ve zaten bir Microsoft 365 E5 planı olan bazı müşterileri içerir:

- **Yeni müşteriler**: 30 günden daha kısa bir süredir Microsoft Purview'unuz varsa, kiracınız listelenen tüm varsayılan yapılandırmaları etkinleştirebilir. Bunları istediğiniz zaman devre dışı bırakabilir, kaldırabilir veya düzenleyebilirsiniz.

- **Mevcut müşteriler**: 30 günden uzun süredir Microsoft Purview'a sahipseniz, henüz eşdeğer bir yapılandırma yapmadıysanız varsayılan yapılandırmaları etkinleştirebilirsiniz:

    | Varsayılan yapılandırma| Eşdeğer |
    |:-----|:-----|
    |Duyarlılık etiketleri ve duyarlılık etiketi ilkesi | Yayımlanan duyarlılık etiketleri |
    |İstemci tarafı otomatik etiketleme | Office uygulamalarında otomatik olarak uygulamak (veya kullanıcılara önermek) için yapılandırılmış bir veya daha fazla duyarlılık etiketi|
    |Hizmet tarafı otomatik etiketleme | Açık olan en az bir otomatik etiketleme ilkesi|
    |Teams için DLP | Teams için en az bir DLP ilkesi|
    |Cihazlar için DLP | Cihazlar için en az bir DLP ilkesi|

## <a name="activate-the-default-labels-and-policies"></a>Varsayılan etiketleri ve ilkeleri etkinleştirme

Önceden yapılandırılmış bu etiketleri ve ilkeleri almak için: 

1. [Microsoft Purview uyumluluk portalından](https://compliance.microsoft.com/) **ÇözümlerFormasyon** >  **koruması'nı** seçin
    
    Bu seçeneği hemen görmüyorsanız, önce gezinti **bölmesinden Tümünü göster'i** seçin. 
    
2. Microsoft Purview Information Protection varsayılan etiketler ve ilkeler için uygunsanız, varsayılan etiketleri ve ilkeleri etkinleştirebileceğiniz aşağıdaki bilgileri görürsünüz. Örneğin:
    
    :::image type="content" alt-text="Microsoft Purview Information Protection önceden yapılandırılmış etiketler ve ilkeler için etkinleştirme." source="../media/mip-preconfigured.png" lightbox="../media/mip-preconfigured.png":::
    
    Etkinleştirme seçeneğiyle birlikte bu bilgilerin görüntülendiğini görmüyorsanız, şu anda duyarlılık etiketlerinin ve ilkelerinin otomatik olarak oluşturulması için uygun değilsiniz demektir. Bu durumun değişip değişmediğini görmek için daha sonra yeniden denetlemeyi deneyebilir veya aynı etiketleri ve ilkeleri el ile oluşturmak için aşağıdaki ayarlar bilgilerini kullanabilirsiniz.

3. Şimdi SharePoint ve OneDrive için duyarlılık etiketlerini etkinleştirin. Bu adım, Web için Office duyarlılık etiketlerini ve SharePoint ve OneDrive için otomatik etiketleme ilkelerini kullanmak için önkoşuldur.
   
    Information Protection **Genel Bakış** sekmesinin üst kısmındaki aşağıdaki başlığı kullanın ve **Şimdi aç'ı** seçin. Bu başlığı görmüyorsanız, kiracınız için SharePoint ve OneDrive duyarlılık etiketleri zaten etkinleştirilmiştir.
    
    ![SharePoint ve OneDrive başlığı için duyarlılık etiketlerini etkinleştirin.](../media/turn-on-mip-labels.png)
    
    Bu özellik hakkında daha fazla bilgi için bkz[. SharePoint ve OneDrive Office dosyaları için duyarlılık etiketlerini etkinleştirme](sensitivity-labels-sharepoint-onedrive-files.md).

## <a name="default-sensitivity-labels"></a>Varsayılan duyarlılık etiketleri

Yayımlanan duyarlılık etiketleriniz olmadığında sizin için aşağıdaki etiketleri oluşturacağız:


|Etiket adı|Kullanıcılar için etiket açıklaması|Ayarlar|
|-------------------------------|---------------------------|-----------------|
|Personal|yalnızca kişisel kullanım için iş dışı veriler.|**Kapsam**: Dosya, E-posta <br /><br />**İçerik işaretleme**: Hayır<br /><br />**Otomatik etiketleme**: Hayır <br /><br />**Grup ayarları**: Hayır<br /><br />**Site ayarları**: Hayır <br /><br />**Veritabanı sütunları için otomatik etiketleme**: Yok|
|Kamu|Özel olarak hazırlanan ve genel tüketim için onaylanan iş verileri.|**Kapsam**: Dosya, E-posta <br /><br />**İçerik işaretleme**: Hayır<br /><br />**Otomatik etiketleme**: Hayır <br /><br />**Grup ayarları**: Hayır<br /><br />**Site ayarları**: Hayır <br /><br />**Veritabanı sütunları için otomatik etiketleme**: Yok|
|Genel|Genel kullanıma yönelik olmayan iş verileri. Ancak bu, gerektiğinde dış iş ortaklarıyla paylaşılabilir. Örnek olarak şirket içi telefon dizini, kuruluş şemaları, iç standartlar ve çoğu iç iletişim verilebilir.|**Kapsam**: Dosya, E-posta <br /><br />**İçerik işaretleme**: Hayır<br /><br />**Otomatik etiketleme**: Hayır <br /><br />**Grup ayarları**: Hayır<br /><br />**Site ayarları**: Hayır <br /><br />**Veritabanı sütunları için otomatik etiketleme**: Yok|
|Genel <br /> \ Herkes (sınırsız)|Genel kullanıma yönelik olmayan ancak uygunsa dış iş ortaklarıyla paylaşılabilen kuruluş verileri. Hassas bilgileri veya piyasaya sürülen pazarlama malzemelerini içermeyen müşteri konuşmaları buna örnek olarak verilebilir.|**Kapsam**: Dosya, E-posta <br /><br />**İçerik işaretleme**: Hayır<br /><br />**Otomatik etiketleme**: Hayır <br /><br />**Grup ayarları**: Hayır<br /><br />**Site ayarları**: Hayır <br /><br />**Veritabanı sütunları için otomatik etiketleme**: Yok|
|Genel <br /> \ Tüm Çalışanlar (sınırsız)|Genel kullanıma yönelik olmayan kuruluş verileri. Bu içeriği dış iş ortaklarıyla paylaşmanız gerekiyorsa, diğer veri sahipleriyle paylaşmanın uygun olduğunu onaylayın ve ardından etiketi Genel \ Herkes (sınırsız) olarak değiştirin. Örnek olarak şirket içi telefon dizini, kuruluş şemaları, iç standartlar ve çoğu iç iletişim verilebilir.|**Kapsam**: Dosya, E-posta <br /><br />**İçerik işaretleme**: Hayır<br /><br />**Otomatik etiketleme**: Hayır <br /><br />**Grup ayarları**: Hayır<br /><br />**Site ayarları**: Hayır <br /><br />**Veritabanı sütunları için otomatik etiketleme**: Yok|
|Gizli|Yetkisiz kişilerle paylaşılırsa işletmenin zarar görmesine neden olabilecek hassas iş verileri. Örnek olarak sözleşmeler, güvenlik raporları, tahmin özetleri ve satış hesabı verileri verilebilir.|**Kapsam**: Dosya, E-posta <br /><br />**İçerik işaretleme**: Hayır<br /><br />**Otomatik etiketleme**: Hayır <br /><br />**Grup ayarları**: Hayır<br /><br />**Site ayarları**: Hayır <br /><br />**Veritabanı sütunları için otomatik etiketleme**: Yok|
|Gizli <br /> \ Herkes (sınırsız)|Şifrelenmemesi gereken gizli veriler. Bu seçeneği dikkatli ve uygun iş gerekçesiyle kullanın.|Bu etiket [, istemci tarafı otomatik etiketleme](#client-side-auto-labeling) ve [hizmet tarafı otomatik etiketleme](#service-side-auto-labeling) için seçilir.<br /><br /> **Kapsam**: Dosya, E-posta <br /><br />**İçerik işaretleme**: Alt Bilgi: Gizli Olarak Sınıflandırılmış<br /><br />**Otomatik etiketleme**: Kullanıcıların etiketi uygulaması önerilir <br /><br />**Grup ayarları**: Hayır<br /><br />**Site ayarları**: Hayır <br /><br />**Veritabanı sütunları için otomatik etiketleme**: Yok|
|Gizli <br /> \ Tüm Çalışanlar|Tüm çalışanların tam izinlere sahip olmasını sağlayan koruma gerektiren gizli veriler. Veri sahipleri içeriği izleyebilir ve iptal edebilir.|Bu etiket [, istemci tarafı otomatik etiketleme](#client-side-auto-labeling) ve [hizmet tarafı otomatik etiketleme](#service-side-auto-labeling) için seçilir.<br /><br /> **Kapsam**: Dosya, E-posta <br /><br />**Şifreleme**: Kuruluştaki tüm kullanıcılar ve gruplar: Co-Author<br /><br />**İçerik işaretleme**: Alt Bilgi: Gizli Olarak Sınıflandırılmış<br /><br />**Otomatik etiketleme**: Kullanıcıların etiketi uygulaması önerilir <br /><br />**Grup ayarları**: Hayır<br /><br />**Site ayarları**: Hayır <br /><br />**Veritabanı sütunları için otomatik etiketleme**: Yok |
|Gizli <br /> \ Güvenilen Kişiler|Kuruluşunuzun içindeki ve dışındaki güvenilir kişilerle paylaşılabilen gizli veriler. Bu kişiler gerektiğinde verileri yeniden paylaşabilir.|**Kapsam**: Dosya, E-posta <br /><br />**Şifreleme**: Kullanıcıların izin atamasına izin verin: <br /> - Outlook için Encrypt-Only <br />- Word, PowerPoint ve Excel'da kullanıcılara sor<br /><br />**İçerik işaretleme**: Alt Bilgi: Gizli Olarak Sınıflandırılmış<br /><br />**Otomatik etiketleme**: Hayır <br /><br />**Grup ayarları**: Hayır<br /><br />**Site ayarları**: Hayır <br /><br />**Veritabanı sütunları için otomatik etiketleme**: Yok|
|Çok Gizli|Yetkisiz kişilerle paylaşıldığında işletmenin zarar görmesine neden olabilecek çok hassas iş verileri. Çalışan ve müşteri bilgileri, parolalar, kaynak kodu ve önceden duyurulan finansal raporlar buna örnek olarak verilebilir.|**Kapsam**: Dosya, E-posta <br /><br />**İçerik işaretleme**: Filigran: ÇOK GİzLİ<br /><br />**Otomatik etiketleme**: Hayır <br /><br />**Grup ayarları**: Hayır<br /><br />**Site ayarları**: Hayır <br /><br />**Veritabanı sütunları için otomatik etiketleme**: Yok|
|Çok Gizli <br /> \ Tüm Çalışanlar|Tüm çalışanların bu içeriği görüntülemesine, düzenlemesine ve yanıtlamasına olanak tanıyan son derece gizli veriler. Veri sahipleri içeriği izleyebilir ve iptal edebilir.|**Kapsam**: Dosya, E-posta <br /><br />**Şifreleme**: Kuruluştaki tüm kullanıcılar ve gruplar: Co-Author<br /><br />**İçerik işaretleme**: Alt Bilgi: Çok Gizli Olarak Sınıflandırılmış<br /><br />**Otomatik etiketleme**: Hayır <br /><br />**Grup ayarları**: Hayır<br /><br />**Site ayarları**: Hayır <br /><br />**Veritabanı sütunları için otomatik etiketleme**: Yok|
|Çok Gizli <br /> \ Belirli Kişiler |Koruma gerektiren ve yalnızca belirttiğiniz kişiler tarafından ve seçtiğiniz izin düzeyiyle görüntülenebilir.|**Kapsam**: Dosya, E-posta <br /><br />**Şifreleme**: Kullanıcıların izin atamasına izin verin: <br />- Outlook İçin İletme <br />- Word, PowerPoint ve Excel'da kullanıcılara sor<br /><br />**İçerik işaretleme**: Alt Bilgi: Çok Gizli Olarak Sınıflandırılmış<br /><br />**Otomatik etiketleme**: Hayır <br /><br />**Grup ayarları**: Hayır<br /><br />**Site ayarları**: Hayır <br /><br />**Veritabanı sütunları için otomatik etiketleme**: Yok|

> [!NOTE]
> Etiket adları ve açıklamaları şu yerel ayarlar için otomatik olarak kullanılabilir: ABD İngilizcesi, Basitleştirilmiş Çince ve Geleneksel, Fransızca, Almanca, İtalyanca, Japonca, Korece, Portekizce Brezilya, Rusça ve İspanyolca.
> 
> Ek dillere ihtiyacınız varsa [, PowerShell kullanarak](create-sensitivity-labels.md#example-configuration-to-configure-a-sensitivity-label-for-different-languages) çevirilerinizi belirtebilirsiniz.

Bu yapılandırma ayarları ve duyarlılık etiketlerinin yapabilecekleri hakkında daha fazla bilgi için bkz. [Duyarlılık etiketlerinin yapabilecekleri](sensitivity-labels.md#what-sensitivity-labels-can-do).

Bu varsayılan duyarlılık etiketlerini düzenlemeniz gerekiyorsa bkz. [Duyarlılık etiketleri oluşturma ve yapılandırma](create-sensitivity-labels.md#create-and-configure-sensitivity-labels).

## <a name="default-sensitivity-label-policy"></a>Varsayılan duyarlılık etiketi ilkesi

Varsayılan duyarlılık etiketi ilkesi, etiketlerin kullanıcıların belge ve e-postalarını duyarlılık etiketleriyle etiketlemeye başlamasını sağlar. Aşağıdaki yapılandırmaya sahiptir:

- Varsayılan etiketleri kiracınızdaki tüm kullanıcılara yayımlama
- Etiketlenmemiş belgeler ve e-postalar için **GenelTüm** \  **Çalışanlar (sınırsız)** varsayılan etiketi
- Kullanıcılar bir etiketi kaldırmak veya sınıflandırmasını düşürmek için bir gerekçe sağlamalıdır

Bu ilke ayarları ve kullanılabilen diğer ilke ayarları hakkında daha fazla bilgi için bkz [. Etiket ilkelerinin yapabilecekleri](sensitivity-labels.md#what-label-policies-can-do).

Bu varsayılan ilke ayarlarını düzenlemeniz gerekiyorsa bkz. Etiket [ilkesi oluşturarak duyarlılık etiketlerini yayımlama](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy).

Bu etiketleri Windows, macOS, iOS ve Android'deki Office uygulamalarında kullandığınızda, kullanıcılar yeni etiketleri dört saat içinde ve tarayıcıyı yenilediğinizde Word, Excel ve Web üzerinde PowerPoint için de bir saat içinde görür. Ancak değişikliklerin tüm uygulama ve hizmetlere çoğaltılması için 24 saate kadar izin vermeniz gerekebilir.

## <a name="client-side-auto-labeling"></a>İstemci tarafı otomatik etiketleme

Varsayılan istemci tarafı otomatik etiketleme yapılandırması, üzerinde çalıştıkları belgelerde veya e-postalarda kredi kartı numaraları algıladığımızda kullanıcıların otomatik olarak duyarlılık etiketi uygulamasını önerir. Bu yapılandırma, otomatik olarak uygulanmak yerine bir öneri olarak, içerikle ilgili vurgulama için iyi bir ilk adımdır ve kullanıcılara belgelerini ve e-postalarını etiketleme uygulamasını tanıtır.

İstemci tarafı otomatik etiketleme yalnızca word, Excel, PowerPoint ve Outlook Office uygulamaları tarafından kullanılan belgeler ve e-postalar için çalışır. 

Varsayılan istemci tarafı otomatik etiketleme aşağıdaki yapılandırmaya sahiptir: 

- Bir belgede veya e-postada 1-9 tane kredi kartı numarası bulunuyorsa, kullanıcının **ConfidentialAnyone**  \  duyarlılık etiketini (sınırsız) uygulamasını öneririz 

- Bir belgede veya e-postada 10 veya daha fazla kredi kartı numarası örneği bulunuyorsa, kullanıcının **GizliTüm**  \  Çalışanlar duyarlılık etiketini uygulamasını öneririz 

> [!NOTE]
> Kendi duyarlılık etiketlerinizin yayımlandığını algıladıysak, otomatik etiketleme için kendi etiketlerinizden birini seçmenizi ve sizin için yapılandırmanızı isteriz.

İstemci tarafı otomatik etiketleme yapılandırmasını düzenlemek istiyorsanız bkz. [Office uygulamaları için otomatik etiketlemeyi yapılandırma](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps).

## <a name="service-side-auto-labeling"></a>Hizmet tarafı otomatik etiketleme 

Hizmet tarafı otomatik etiketleme, bekleyen hassas belgelerin ve aktarım sırasındaki e-postaların etiketlenmesine yardımcı olur. Varsayılan hizmet tarafı otomatik etiketleme ilkesi, tüm SharePoint veya OneDrive sitelerinde depolanan belgeler ve Exchange Online aracılığıyla gönderilen tüm e-postalar için simülasyon modunda bir ilke oluşturur. Simülasyon modunda, ilkeyi etkinleştirene kadar öğeler aslında etiketlenmez. Simülasyon modu, ilke açıldığında hangi öğelerin etiketlendiğini önizlemenize olanak tanır, böylece ilkeyi kiracınıza gerçek etiketleme için dağıtmadan önce etiketleme özelliğine güvenirsiniz. 

Varsayılan hizmet tarafı otomatik etiketleme aşağıdaki yapılandırmaya sahiptir: 

- Belgede 1-9 tane kredi kartı numarası bulunuyorsa **, ConfidentialAnyone** \  duyarlılık etiketini **(sınırsız)** uygulayın

- Bir belgede veya e-postada 10 veya daha fazla kredi kartı numarası örneği bulunuyorsa, kullanıcının **GizliTüm**  \  Çalışanlar duyarlılık etiketini uygulamasını öneririz 

> [!NOTE]
> Kendi duyarlılık etiketlerinizin yayımlandığını algıladıysak, otomatik etiketleme ilkeniz için kendi etiketlerinizden birini seçmenizi isteriz.

Simülasyon tamamlandığında sonuçları gözden geçirin ve onlardan memnunsanız ilkeyi açın.

Simülasyon modu hakkında daha fazla bilgi için bkz. [Simülasyon modu hakkında bilgi edinin](apply-sensitivity-label-automatically.md#learn-about-simulation-mode).

Hizmet tarafı otomatik etiketleme ilkesini düzenlemek istiyorsanız bkz. [SharePoint, OneDrive ve Exchange için otomatik etiketleme ilkelerini yapılandırma](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange).

## <a name="dlp-for-teams"></a>Teams için DLP

Teams için varsayılan DLP ilkesi, tüm Teams sohbetlerinde ve kanal iletilerinde kredi kartı numaralarının varlığını algılar. Bu hassas bilgiler algılandığında yöneticiler düşük önem derecesine sahip bir uyarı bildirimi alır.

Bu ilke, ilke ipucu görünmeyen ve ileti engellenmeyen kullanıcılar için dikkat çekmez, ancak yöneticiler bu iletilerde paylaşılan hassas bilgilerin kayıtlarına sahip olur. Gerekirse, bu varsayılan yapılandırmayı değiştirmek için ayarları düzenleyebilirsiniz.

Bu ilkenin sonuçlarını görmek için [DLP Etkinlik Gezgini'ni](dlp-learn-about-dlp.md#dlp-activity-explorer) kullanın.

DLP ilkesini düzenlemek istiyorsanız bkz. [DLP ilkesi oluşturma, test etme ve ayarlama](create-test-tune-dlp-policy.md).

## <a name="dlp-for-devices"></a>Cihazlar için DLP

Cihazlar için varsayılan DLP ilkesi, Microsoft Purview'a eklenmiş Windows 10 cihazlarda kredi kartı numaralarının bulunduğunu algılar. Ardından aşağıdaki eylemleri denetler (engellemez): 

- Bulut hizmeti etki alanlarına Upload veya izin verilmeyen tarayıcılar tarafından erişim

- Panoya, USB'ye veya ağ paylaşımına kopyalama 

- İzin verilmeyen uygulamalarla erişim 

- Yazdırma 

- İzin verilmeyen Bluetooth uygulamasını kullanarak kopyalama veya taşıma 

- Uzak masaüstü hizmetleri 

İçerikte 10 veya daha fazla kredi kartı örneği varsa ve listelenen etkinliklerden biri veya daha fazlası algılanırsa, yöneticilere orta önem derecesi uyarı bildirimi gönderilir.

Bu ilke, hiçbir ilke ipucu görünmeyen ve hiçbir eylem engellenmeyen kullanıcılar için dikkat çekmez, ancak yöneticiler tüm şüpheli etkinliklerin kayıtlarına sahip olur. Gerekirse, bu varsayılan yapılandırmayı değiştirmek için bu ayarları düzenleyebilirsiniz.

Bu ilkenin sonuçlarını görmek için [DLP Etkinlik Gezgini'ni](dlp-learn-about-dlp.md#dlp-activity-explorer) kullanın.

DLP ilkesini düzenlemek istiyorsanız bkz. [DLP ilkesi oluşturma, test etme ve ayarlama](create-test-tune-dlp-policy.md).

## <a name="additional-resources"></a>Ek kaynaklar

Duyarlılık etiketleri, veri kaybı önleme ve Microsoft Purview Information Protection ile sağlanan tüm özellikler hakkında daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [Duyarlılık etiketleri hakkında bilgi edinin](sensitivity-labels.md)
- [Veri kaybı önleme hakkında daha fazla bilgi edinme](dlp-learn-about-dlp.md)
- [Microsoft Purview ile verilerinizi koruma](information-protection.md)
