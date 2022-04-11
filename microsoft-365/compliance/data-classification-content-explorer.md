---
title: İçerik gezginini kullanmaya başlama
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
ms.openlocfilehash: 0a3b036a60d3ec24533056b38ff1e68be9875aa0
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64761383"
---
# <a name="get-started-with-content-explorer"></a>İçerik gezginini kullanmaya başlama

Veri sınıflandırması içerik gezgini, genel bakış sayfasında özetlenen öğeleri yerel olarak görüntülemenizi sağlar.

![içerik gezgini daraltılmış ekran görüntüsü.](../media/data-classification-content-explorer-1.png)

## <a name="prerequisites"></a>Önkoşullar

Lisans gereksinimleri için bkz[. Information Protection: Veri Sınıflandırma Analizi: Genel Bakış İçerik & Etkinlik Gezgini](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-classification-analytics-overview-content--activity-explorer)

### <a name="permissions"></a>İzinler

İçerik gezgini sekmesine erişim elde etmek için, bu rollerden veya rol gruplarından herhangi birinde bir hesaba üyelik atanmalıdır. 

**rol gruplarını Microsoft 365**

- Genel yönetici
- Uyumluluk yöneticisi
- Güvenlik yöneticisi
- Uyumluluk veri yöneticisi

> [!IMPORTANT]
> Bu rol gruplarındaki üyelik, içerik gezginindeki öğelerin listesini görüntülemenize veya içerik gezginindeki öğelerin içeriğini görüntülemenize izin vermez.

> [!IMPORTANT]
> Uyumluluk Merkezi'ndeki diğer kullanıcıları yalnızca Genel yöneticiler yönetebilir veya bu kullanıcılara izin atayabilir. Diğer ayrıntılar için bkz. [Kullanıcılara Güvenlik & Uyumluluk Merkezi'ne erişim verme](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).
> 
### <a name="required-permissions-to-access-items-in-content-explorer"></a>İçerik gezginindeki öğelere erişmek için gerekli izinler

Taranan dosyaların içeriğini okumanıza olanak sağladığından içerik gezginine erişim yüksek oranda kısıtlanmıştır.

> [!IMPORTANT]
> Bu izinler, öğelere yerel olarak atanan ve içeriğin görüntülenmesine izin veren izinlerin yerini alır. 

İçerik gezginine erişim veren iki rol vardır ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">Microsoft 365 uyumluluk merkezi</a> kullanılarak verilir:

- **İçerik Gezgini Liste görüntüleyicisi**: Bu rol grubundaki üyelik, liste görünümünde her öğeyi ve konumunu görmenizi sağlar. Rol `data classification list viewer` , bu rol grubuna önceden atanmıştır.

- **İçerik Gezgini İçerik görüntüleyicisi**: Bu rol grubundaki üyelik, listedeki her öğenin içeriğini görüntülemenizi sağlar. Rol `data classification content viewer` , bu rol grubuna önceden atanmıştır.

İçerik gezginine erişmek için kullandığınız hesap rol gruplarından birinde veya her ikisinde olmalıdır. Bunlar bağımsız rol gruplarıdır ve kümülatif değildir. Örneğin, bir hesaba öğeleri ve yalnızca konumlarını görüntüleme olanağı vermek istiyorsanız İçerik Gezgini Listesi görüntüleyicisi hakları verin. Aynı hesabın listedeki öğelerin içeriğini de görüntüleyebilmesini istiyorsanız, İçerik Gezgini İçerik görüntüleyicisi haklarını da verin.

Ayrıca, içerik gezginine erişimi uyarlamak için rollerin birini veya her ikisini de özel bir rol grubuna atayabilirsiniz.

Genel yönetici, gerekli İçerik Gezgini Liste Görüntüleyicisi'ni ve İçerik Gezgini İçerik Görüntüleyicisi rol grubu üyeliğini atayabilir.

#### <a name="roles-and-role-groups-in-preview"></a>Önizlemede Roller ve Rol Grupları

Önizlemede, erişim denetimlerinizde ince ayar yapmak için test yapabileceğiniz roller ve rol grupları vardır.

Önizleme aşamasında olan Microsoft Bilgi Koruması (MIP) rollerinin listesi aşağıdadır. Bunlar hakkında daha fazla bilgi edinmek için bkz [. Güvenlik & Uyumluluk Merkezi'ndeki Roller](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Information Protection Yöneticisi
- Information Protection Analisti
- Information Protection Araştırmacısı
- Information Protection Okuyucu

Önizleme aşamasında olan MIP rol gruplarının listesi aşağıdadır. Daha fazla bilgi için bkz [. Güvenlik & Uyumluluk Merkezi'nde rol grupları](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Information Protection
- Information Protection Yöneticileri
- Information Protection Analistleri
- Information Protection Araştırmacıları
- Information Protection Okuyucular

## <a name="content-explorer"></a>İçerik gezgini

İçerik gezgini duyarlılık etiketine, bekletme etiketine sahip veya kuruluşunuzda hassas bilgi türü olarak sınıflandırılmış öğelerin geçerli anlık görüntüsünü gösterir.

### <a name="sensitive-information-types"></a>Hassas bilgi türleri

[DLP ilkesi](dlp-learn-about-dlp.md), hassas bilgi türü olarak tanımlanan **hassas bilgilerin** korunmasına yardımcı olabilir. Microsoft 365, birçok farklı bölgeden kullanıma hazır [birçok ortak hassas bilgi türü için tanımlar](sensitive-information-type-entity-definitions.md) içerir. Örneğin, kredi kartı numarası, banka hesap numaraları, ulusal kimlik numaraları ve Windows Canlı Kimlik hizmet numaraları.

### <a name="sensitivity-labels"></a>Duyarlılık etiketleri

[Duyarlılık etiketi](sensitivity-labels.md), öğenin kuruluşunuzdaki değerini gösteren bir etikettir. El ile veya otomatik olarak uygulanabilir. Uygulandıktan sonra etiket belgeye eklenir ve belgenin gittiği her yerde belgeyi izler. Duyarlılık etiketi, zorunlu filigran veya şifreleme gibi çeşitli koruyucu davranışlar sağlar.

İlgili verilerin veri sınıflandırma sayfasında gösterilmesi için SharePoint ve OneDrive dosyalar için duyarlılık etiketleri etkinleştirilmelidir. Daha fazla bilgi için bkz[. SharePoint ve OneDrive Office dosyaları için duyarlılık etiketlerini etkinleştirme](sensitivity-labels-sharepoint-onedrive-files.md).

### <a name="retention-labels"></a>Bekletme etiketleri

[Bekletme etiketi,](retention.md) etiketlenmiş bir öğenin ne kadar süreyle tutulacağı ve silinmeden önce izlenecek adımları tanımlamanıza olanak tanır. Bunlar, ilkeler aracılığıyla el ile veya otomatik olarak uygulanır. Kuruluşunuzun yasal ve mevzuat gereksinimleriyle uyumlu kalmasına yardımcı olmak için bir rol oynayabilirler.

### <a name="how-to-use-content-explorer"></a>İçerik gezginini kullanma

1. **Microsoft 365 uyumluluk merkezi**  >  **Data** **classificationContent** >  gezginini açın.
2. Etiketin adını veya hassas bilgi türünü biliyorsanız, bunu filtre kutusuna yazabilirsiniz.
3. Alternatif olarak, etiket türünü genişletip listeden etiketi seçerek öğeye göz atabilirsiniz.
4. **Tüm konumlar'ın** altında bir konum seçin ve öğedeki klasör yapısının detayına gidin.
5. Öğeyi içerik gezgininde yerel olarak açmak için çift tıklayın.

### <a name="export"></a>Dışarı aktarma
Dışarı **aktarma** denetimi **, Tüm konumlar** bölmesinde gösterilenlerin listesini içeren bir .csv dosyası oluşturur.

![veri sınıflandırması dışarı aktarma denetimi.](../media/data_classification_export_control.png)


> [!NOTE]
> İçerik gezgininde sayıların güncelleştirilmiş olması *yedi güne* kadar sürebilir.

### <a name="search"></a>Arama

Exchange veya Teams klasörü ya da SharePoint ya da OneDrive sitesi gibi bir konumda detaya gittiğiniz zaman **arama** aracı görüntülenir.

![içerik gezgini arama aracı.](../media/data_classification_search_tool.png)

Arama aracının kapsamı **Tüm konumlar** bölmesinde görüntülenen araçtır ve arama yapabileceklerin seçilen konuma bağlı olarak değişir. 

**Seçilen konum Exchange** veya **Teams** olduğunda, örneğin `user@domainname.com`posta kutusunun tam e-posta adresini arayabilirsiniz.

**konum SharePoint** veya **OneDrive** seçildiğinde, site adları, klasörleri ve dosyalarında detaya gittiğiniz zaman arama aracı görüntülenir. 

Arama yapabileceğiniz yer:

|Değer|Örnek  |
|---------|---------|
|tam site adı    |`https://contoso.onmicrosoft.com/sites/sitename`    |
|dosya adı    |    `RES_Resume_1234.txt`     |
|dosya adının başındaki metin| `RES`|
|dosya adında bir alt çizgi karakteri ( _ ) sonra gelen metin|`Resume` Veya `1234`| 
|dosya uzantısı|`txt`|


## <a name="see-also"></a>Ayrıca bkz.

- [Duyarlılık etiketleri hakkında bilgi edinin](sensitivity-labels.md)
- [Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi edinin](retention.md)
- [Hassas bilgi türü varlığı definitions.md](sensitive-information-type-entity-definitions.md)
- [Veri kaybı önleme hakkında daha fazla bilgi edinme](dlp-learn-about-dlp.md)
