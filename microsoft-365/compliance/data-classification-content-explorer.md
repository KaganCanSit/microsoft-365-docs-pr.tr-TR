---
title: İçerik gezginiyle çalışmaya başlama
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: İçerik gezgini etiketli öğeleri yerel olarak görüntülemenizi sağlar.
ms.openlocfilehash: 61d262c04d4a304506bc521d155be71f81d219ca
ms.sourcegitcommit: 9af389e4787383cd97bc807f7799ef6ecf0664d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2022
ms.locfileid: "63468768"
---
# <a name="get-started-with-content-explorer"></a>İçerik gezginiyle çalışmaya başlama

Veri sınıflandırması içerik gezgini, genel bakış sayfasında özetlenmiş olan öğeleri yerel olarak görüntülemenizi sağlar.

![içerik gezgini daraltılmış ekran görüntüsü.](../media/data-classification-content-explorer-1.png)

## <a name="prerequisites"></a>Önkoşullar

Veri sınıflandırmaya erişen ve kullanan her hesaba, şu aboneliklerden birinin lisansı atanmış olması gerekir:

- Microsoft 365 (E5)
- Office 365 (E5)
- Gelişmiş Uyumluluk (E5) eklenti
- Gelişmiş Tehdit zekası (E5) eklentisi
- Microsoft 365 E5/A5 Bilgi Koruması & Yönetimi
- Microsoft 365 E5/A5 Uyumluluğu


### <a name="permissions"></a>İzinler

İçerik gezgini sekmesine erişim elde etmek için, bu rollerden veya rol gruplarından herhangi biri için bir hesaba üyelik atanabilir. 

**Microsoft 365 grupları**

- Genel yönetici
- Uyumluluk yöneticisi
- Güvenlik yöneticisi
- Uyumluluk veri yöneticisi

> [!IMPORTANT]
> Bu rol gruplarında üyelik, içerik gezgininde öğe listesini görüntülemeye veya içerik gezgininde öğelerin içeriğini görüntülemeye izin vermez.

> [!IMPORTANT]
> Uyumluluk Merkezi'nde yalnızca Genel yöneticiler diğer kullanıcıları yönetebilir veya bu kullanıcılara izin atayabilirsiniz. Diğer ayrıntılar için bkz. [Kullanıcılara Güvenlik ve Uyumluluk Merkezi'& verme](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).
> 
### <a name="required-permissions-to-access-items-in-content-explorer"></a>İçerik gezgininde öğelere erişim için gerekli izinler

Taranan dosyaların içeriğini okumanıza izin olduğundan, içerik gezginine erişim son derece kısıtlıdır.

> [!IMPORTANT]
> Bu izinler, içeriği görüntülemeye olanak sağlayan, öğelere yerel olarak atanmış olan izinlerin yerine dolar. 

İçerik gezginine erişim izni verilen iki rol vardır ve bu rol aşağıdaki <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">Microsoft 365 uyumluluk merkezi:</a>

- **İçerik Gezgini Liste görüntüleyicisi**: Bu rol grubu üyeliği, her öğeyi ve konumunu liste görünümünde görmenizi sağlar. Rol `data classification list viewer` , bu rol grubuna önceden atanmıştır.

- **İçerik Gezgini İçerik görüntüleyicisi**: Bu rol grubu üyeliği, listeden her öğenin içeriğini görüntülemenizi sağlar. Rol `data classification content viewer` , bu rol grubuna önceden atanmıştır.

İçerik gezginine erişmek için kullanabileceğiniz hesap, rol gruplarından birinin veya her ikisinin içinde yer alamaktadır. Bunlar bağımsız rol gruplarıdır ve kümülatif değildir. Örneğin, bir hesaba yalnızca öğeleri ve konumlarını görüntüleme izni vermek için, İçerik Gezgini Listesi görüntüleyici hakları verebilirsiniz. Aynı hesabın aynı zamanda listede yer alan öğelerin içeriğini de görüntüley istemeniz için, İçerik Gezgini İçerik görüntüleyicisi hakları da verebilirsiniz.

Ayrıca, içerik gezginine erişimi uyarlamak için rollerin birini veya her ikisini de özel bir rol grubuna atabilirsiniz.

Genel yönetici, gerekli İçerik Gezgini Liste Görüntüleyicisi'ni ve İçerik Gezgini İçerik Görüntüleyicisi rol grubu üyeliğini atayabilirsiniz.

#### <a name="roles-and-role-groups-in-preview"></a>Önizlemede Roller ve Rol Grupları

Önizlemede, erişim denetimlerinize ince ayar yapmak için test etmek için deney erişiminiz olan roller ve rol grupları vardır.

İşte önizlemede olan Microsoft Bilgi Koruması (MIP) rollerinin listesi. Bu roller hakkında daha fazla bilgi edinmek [için Güvenlik ve Uyumluluk Merkezi'& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Bilgi Koruması Yöneticisi
- Bilgi Koruma Analisti
- Bilgi Koruma Koruma Koruma Koruması
- Bilgi Koruma Okuyucusu

Önizlemede olan MIP rol gruplarının listesi burada ve ve şekildedir. Daha fazla bilgi edinmek için [Güvenlik ve Uyumluluk Merkezi'nde rol & bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center).

- Bilgi Koruması
- Bilgi Koruması Yöneticileri
- Bilgi Koruma Analistleri
- Bilgi Koruma Koruma KorumaLarı
- Bilgi Koruma Okuyucuları

## <a name="content-explorer"></a>İçerik gezgini

İçerik gezgini duyarlılık etiketi, bekletme etiketi veya kuruluşta hassas bir bilgi türü olarak sınıflandırılmış öğelerin geçerli anlık görüntüsünü gösterir.

### <a name="sensitive-information-types"></a>Hassas bilgi türleri

[DLP ilkesi,](dlp-learn-about-dlp.md) hassas bir bilgi türü olarak tanımlanan hassas bilgilerin **korunmasına yardımcı olabilir**. Microsoft 365, [farklı bölgelerden](sensitive-information-type-entity-definitions.md) kullanıma hazır birçok yaygın hassas bilgi türüne ilişkin tanımları içerir. Örneğin, kredi kartı numarası, banka hesabı numaraları, ulusal kimlik numaraları ve canlı Windows numaraları.

### <a name="sensitivity-labels"></a>Duyarlılık etiketleri

Duyarlılık [etiketi yalnızca](sensitivity-labels.md) , öğenin kuruluş değerine işaret gösteren bir etikettir. El ile veya otomatik olarak uygulanabilir. Uygulandıktan sonra belgeye katıştır olur ve gittiği her yerde belgeyi takip eder. Duyarlılık etiketi zorunlu filigran veya şifreleme gibi çeşitli koruyucu davranışlara olanak sağlar.

Duyarlılık etiketlerinin, ilgili verilerin veri sınıflandırma sayfasında SharePoint OneDrive için metin veya metin olarak yer alan dosyalar için etkinleştirilmesi gerekir. Daha fazla bilgi için bkz[. Dosya ve klasörlerin Office için duyarlılık SharePoint OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

### <a name="retention-labels"></a>Bekletme etiketleri

Bekletme [etiketi,](retention.md) etiketli bir öğenin ne kadar süre tutul tutul olacağını ve silmeden önce atılması gereken adımları tanımlamanız için olanak sağlar. Bunlar ilkeler yoluyla el ile veya otomatik olarak uygulanır. Bu organizasyon, yasal ve mevzuat gereksinimleriyle uyumlu kalmasını sağlarken rol oynayabilir.

### <a name="how-to-use-content-explorer"></a>İçerik gezgini nasıl kullanılabilir?

1.   >  Microsoft 365 uyumluluk merkezi **Data classificationContent** >  **explorer'ı açın**.
2. Etiketin adını veya hassas bilgi türünü biliyorsanız, filtre kutusuna bunu girebilirsiniz.
3. Alternatif olarak, etiket türünü genişleterek ve listeden etiketi seçerek öğeye göz atabilirsiniz.
4. Tüm konumlar altında **bir konum seçin** ve öğenin klasör yapısında detaya gidin.
5. Öğeyi içerik gezgininde yerel olarak açmak için çift tıklayın.

### <a name="export"></a>Dışarı aktarma
Dışarı **aktarma** denetimi, .csv konumları bölmesinde gösterilenlerin listesini içeren bir .csv **dosyası oluşturmanızı** sağlar.

![veri sınıflandırması dışarı aktarma denetimi.](../media/data_classification_export_control.png)


> [!NOTE]
> Sayımların içerik *gezgininde* güncelleştirilmiş olması yedi gün kadar da olabilir.

### <a name="search"></a>Arama

Exchange veya Teams klasörü ya da SharePoint veya OneDrive gibi bir konuma detaya gidin; **arama aracı görüntülenir**.

![içerik gezgini arama aracı.](../media/data_classification_search_tool.png)

Arama aracının kapsamı, Tüm konumlar bölmesinde ne görüntüleniyor  ve ne üzerinde arama seçtiğiniz konuma bağlı olarak değişiklik gösterir. 

Seçilen **Exchange** posta **Teams** posta `user@domainname.com`kutusunun tam e-posta adresine, örneğin.

Seçilen **SharePoint** veya **OneDrive** biri seçildiğinde, site adlarına, klasörlerine ve dosyalarına detaya gidin; arama aracı görüntülenir. 

Şu adreste arama:

|değer|örnek  |
|---------|---------|
|tam site adı    |`https://contoso.onmicrosoft.com/sites/sitename`    |
|dosya adı    |    `RES_Resume_1234.txt`     |
|dosya adının başındaki metin| `RES`|
|dosya adı olarak alt çizgi karakteri ( _ ) sonra gelen metin|`Resume` veya `1234`| 
|dosya uzantısı|`txt`|


## <a name="see-also"></a>Ayrıca bkz.

- [Duyarlılık etiketleri hakkında bilgi edinin](sensitivity-labels.md)
- [Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi](retention.md)
- [Hassas bilgi türü varlık definitions.md](sensitive-information-type-entity-definitions.md)
- [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md)
