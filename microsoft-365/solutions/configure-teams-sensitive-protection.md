---
title: Hassas veriler için korumayla ekipleri yapılandırma
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- m365solution-3tiersprotection
- m365solution-securecollab
ms.custom:
- Ent_Solutions
- admindeeplinkSPO
recommendations: false
description: Hassas veriler için korumayla ekipleri dağıtmayı öğrenin.
ms.openlocfilehash: 51e4c3b13d1a54e4edcfd9926ae246dde7d7e3e4
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2022
ms.locfileid: "63712709"
---
# <a name="configure-teams-with-protection-for-sensitive-data"></a>Hassas veriler için korumayla ekipleri yapılandırma

Bu makalede, hassas bir koruma düzeyi için bir ekip ayarlamayı istiyoruz. Bu makaledeki adımları uygulamadan önce, Ekipleri taban [çizgisi](configure-teams-baseline-protection.md) korumasıyla dağıtma makalesinde yer alan adımları tamamlamış olun. Hassas katman, taban çizgisi katmanı üzerinde aşağıdaki ek korumaları sağlar:

- Ekip için, konuk paylaşımını açma ve kapatmaya olanak sağlayan ve kolay SharePoint içeriği web'e erişimi sınırlayan bir duyarlılık etiketi. Bu etiket dosyaları sınıflandırmak için de kullanılabilir.
- Daha kısıtlayıcı bir varsayılan paylaşım bağlantı türü
- Yalnızca ekip sahipleri özel kanallar oluşturabilir.

## <a name="video-demonstration"></a>Video tanıtımı

Bu makalede açıklanan yordamları ayrıntılı olarak izlemek için bu videoyu izleyin.
<br>
<br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4NMS6]

## <a name="guest-sharing"></a>Konuk paylaşımı

İşletmenizin yapısına bağlı olarak, hassas veriler içeren ekipler için konuk paylaşımını etkinleştirmek veya etkinleştirmek istemeyebilirsiniz. Ekipte, kuruluş dışından kişilerle işbirliği yapmayı planlıyorsanız, konuk paylaşımını etkinleştirmenizi öneririz. Microsoft 365 hassas içeriği güvenli bir şekilde paylaşmanıza yardımcı olmak için çeşitli güvenlik ve uyumluluk özellikleri içerir. Bu genellikle, içeriği doğrudan kuruluş dışındakilere e-postayla göndermekten daha güvenli bir seçenektir.

Konuklarla güvenli bir şekilde paylaşma hakkında ayrıntılı bilgi için aşağıdaki kaynaklara bakın:

- [Kuruluş dışından kişilerle paylaşım sırasında dosyalarda yanlışlıkla açık kalma sürelerini sınırlama](./share-limit-accidental-exposure.md)
- [Güvenli bir konuk paylaşım ortamı oluşturma](./create-secure-guest-sharing-environment.md)

Konuk paylaşımına izin vermek veya engellemek için, her ikisi de daha sonra ele alınarak, ekip için bir duyarlılık etiketi ve ilişkili site SharePoint denetimlerini kullanırız.

## <a name="sensitivity-labels"></a>Duyarlılık etiketleri

Hassas koruma düzeyi için ekibi sınıflandırmak için bir duyarlılık etiketi kullan kullan istiyoruz. Bu etiket bu veya diğer ekiplerde ya da ekipler veya ekipler gibi başka dosya konumlarında tek tek dosyaları sınıflandırmak SharePoint OneDrive. 

İlk adım olarak, sizin için duyarlılık etiketlerini etkinleştirmeniz Teams. Ayrıntılar [için bkz. Microsoft Teams'ta, gruplarda Office 365 ve sitelerde içeriği SharePoint duyarlılık etiketleri](../compliance/sensitivity-labels-teams-groups-sites.md) kullanma.

Zaten kuruluşta dağıtılmış duyarlılık etiketleriniz varsa, bu etiketin genel etiket stratejinize nasıl uyduğunu düşünün. Gerekirse, kuruluşun  ihtiyaçlarını karşılamak için adı veya ayarları değiştirebilirsiniz.

Daha sonra için duyarlılık etiketlerini etkinleştirdikten Teams, bir sonraki adım etiketi oluşturmaktır.

Duyarlılık etiketi oluşturmak için
1. Dosyayı [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com).
2. **Çözümler'in** altında Bilgi **koruma'ya tıklayın**.
3. Etiket **oluştur'a tıklayın**.
4. Etikete bir ad verme. **Hassas'ı** öneririz, ancak bu ad zaten kullanıyorsa farklı bir ad seçebilirsiniz.
5. Bir görünen ad ve açıklama ekleyin ve ardından Sonraki'ye **tıklayın**.
6. Bu **etiketin kapsamını tanımla sayfasında** E-postalarda ve **Gruplarda & öğesini** **seçin ve &'a** **tıklayın**.
7. Dosyalar ve **e-postalar için koruma ayarlarını seçin sayfasında** , Sonraki'ye **tıklayın**.
8. Dosyalar ve *e-postalar için otomatik etiketleme** sayfasında, Sonraki'yi **tıklatın**.
9. Gruplar ve **siteler için koruma ayarlarını tanımla sayfasında** Gizlilik ve dış kullanıcı  erişimi ayarları ile Cihaz erişimi ve dış paylaşım ayarları'ı seçin ve **Ardından** Sonraki'ye **tıklayın**.
10. Gizlilik ve **dış kullanıcı erişimi ayarlarını tanımla sayfasında** , **Gizlilik'in altında** Özel **seçeneğini** belirtin.
11. Konuk erişimine izin vermek için Dış kullanıcı erişimi'nin altında **Grup** sahiplerinin Microsoft 365 dışından kişilerini gruba konuk olarak eklemesine **izin ver'i seçin**.
12. **İleri**'ye tıklayın.
13. Dış paylaşımı **ve cihaz erişim ayarlarını tanımla sayfasında, Site** etiketli **dış paylaşımı SharePoint seçin**.
14. Konuk **erişimine izin ediyorsanız** **İçerikle** paylaşılacak kişiler'in altında Yeni ve var olan konuklar'ı veya Bu seçeneğin altındaki **Yalnızca kuruluşta yer alan kişiler'i** seçin.
15. **Unmanaged devices from access altında Allow** **limited, web-only access'i seçin**.
16. **İleri**'ye tıklayın.
17. Veritabanı **sütunları için otomatik etiketleme sayfasında, Sonraki'yi** **tıklatın**.
18. Etiket **oluştur'a** ve ardından **Bitti'ye tıklayın**.

Etiketi oluşturduktan sonra, bunu kullanacak kullanıcılara yayımlamanız gerekir. Hassas koruma için etiketi tüm kullanıcılarına kullandık. Etiketi, Bilgi koruma Microsoft 365 uyumluluk merkezi **Etiket ilkeleri sekmesinde yayımlarsiniz****.** Tüm kullanıcılar için geçerli olan bir ilkeniz varsa, bu etiketi bu ilkeye ekleyin. Yeni bir ilke oluşturmanız gerekirse, bkz. [Etiket ilkesi oluşturarak duyarlılık etiketlerini yayımlama](../compliance/create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy).

## <a name="create-a-team"></a>Ekip oluşturma

Hassas senaryonun yapılandırmasını daha fazla SharePoint ekiple ilişkilendirilmiş olan ekip sitesinde yapılır; dolayısıyla bir sonraki adım ekip oluşturmaktır.

Hassas bilgiler için ekip oluşturmak için
1. Ekip Teams, **uygulamanın Teams** tarafındaki Ekip Ekle'ye tıklayın ve ekip listesinin alt kısmından Takıma katıl  veya ekip oluştur'a tıklayın.
2. Ekip **oluştur'a** (ilk kart, sol üst köşede) tıklayın.
3. **Sıfırdan ekip oluşturma'yi seçin**.
4. Duyarlılık **listesinde** , yeni oluşturduğunuz **hassas** etiketi seçin.
5. **Gizlilik'in** altında **Özel'e tıklayın**.
6. Ekip için bir ad yazın ve Oluştur'a **tıklayın**.
7. Ekseta kullanıcı ekleyin ve Kapat'a **tıklayın**.

## <a name="private-channel-settings"></a>Özel kanal ayarları

Bu katmanda, özel kanallar oluşturmayı ekip sahipleri ile kısıtlarız.

Özel kanal oluşturma kısıtlamak için
1. Ekipte Diğer **seçenekler'e ve sonra** da Ekibi yönet'e **tıklayın**.
2. Ekle **Ayarlar** Üye **izinleri'ne tıklayın**.
3. Üyelerin **özel kanal oluşturmasına izin ver onay** kutusunu temizleyin.

Ayrıca, kimlerin özel [kanal oluştura](/MicrosoftTeams/teams-policies) onu kontrol etmek için ekip ilkelerini de kullanabilirsiniz.

## <a name="shared-channel-settings"></a>Paylaşılan kanal ayarları

[Paylaşılan kanalların](/MicrosoftTeams/shared-channels) ekip düzeyi ayarları yok. Hem yönetim merkezinde hem de Azure AD'de Teams paylaşılan kanal ayarları duyarlılık ne olursa olsun tüm ekiplere uygulanır.

## <a name="sharepoint-settings"></a>SharePoint ayarları

Her yeni ekip 2013'te hassas etikete sahip yeni bir ekip  oluşturmanız SharePoint:

- Varsayılan paylaşım bağlantısını Belirli kişiler olarak güncelleştirmek için SharePoint yönetim merkezinde sitenin konuk paylaşım *ayarlarını güncelleştirin*.
- Üyelerin siteyi paylaşmasını engellemek için sitenin kendisinde site paylaşım ayarlarını güncelleştirin.

### <a name="site-default-sharing-link-settings"></a>Site varsayılan paylaşım bağlantısı ayarları

Site varsayılan paylaşım bağlantı türünü güncelleştirmek için

1. Site yönetim SharePoint açın ve **Siteler'in altında Etkin** <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**siteler'i seçin**</a>.
1. Ekiple ilişkilendirilmiş siteyi seçin.
1. **İlkeler sekmesinde**, Dış **paylaşım'ın altında** Düzenle'ye **tıklayın**.
1. Varsayılan paylaşım bağlantı türü'nin altında Kuruluş  düzeyi ayarıyla aynı onay kutusunu temizleyin ve Belirli kişiler **(yalnızca kullanıcının paylaştığı kişiler) öğesini seçin**.
1. **Kaydet**'i seçin.

Bunu ekip oluşturma işleminizin bir parçası olarak kullanmak için [Set-SPOSite'i](/powershell/module/sharepoint-online/set-sposite) `-DefaultSharingLinkType Direct` parametreyle birlikte kullanabilir ve varsayılan paylaşım bağlantısını Belirli kişiler *olarak değiştirebilirsiniz*.

Ek ekiplere özel veya paylaşılan kanallar eklerken her biri varsayılan paylaşım SharePoint yeni bir site oluşturur. Ekiple ilişkili siteleri SharePoint yönetim merkezinden güncelleştirebilirsiniz.

### <a name="site-sharing-settings"></a>Site paylaşım ayarları

Sitenin, SharePoint üyesi değil kişileriyle paylaşılmaması için, bu paylaşımı sahiplerle sınırlandırdık. Bu yalnızca ekiple SharePoint site için gereklidir. Özel veya paylaşılan kanalların bir parçası olarak oluşturulan diğer siteler ekip veya kanalın dışında paylaşılamaz.

Yalnızca sahipler için site paylaşımını yapılandırmak için
1. Güncelleştirme Teams, güncelleştirmek **istediğiniz** ekibin Genel sekmesine gidin.
2. Ekibin araç çubuğunda Dosyalar'a **tıklayın**.
3. Üç noktayı tıklatın ve sonra Üç **Nokta'da Aç'ı SharePoint**.
4. Temel sitenin araç çubuğunda SharePoint simgesine tıklayın ve sonra da Site **izinleri'ne tıklayın**.
5. Site izinleri **bölmesinde,** Site **paylaşımı'nın altında** Üyelerin **paylaşımlarını değiştir'e tıklayın**.
6. Paylaşım **izinleri'nin** altında **Site sahipleri** ve üyeleri'ne tıklayın; Düzenleme izinleri olan kişiler dosyaları ve klasörleri paylaşabilir; ancak yalnızca site sahipleri siteyi paylaşabilir ve Kaydet'e **tıklayın**.


## <a name="related-topics"></a>İlgili konular

[Duyarlılık etiketlerini ve onların ilkelerini oluşturma ve yapılandırma](../compliance/create-sensitivity-labels.md)
