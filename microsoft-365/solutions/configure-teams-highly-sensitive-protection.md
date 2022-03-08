---
title: Çok hassas veriler için ekipleri koruma ile yapılandırma
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
description: Çok hassas veriler için korumayla ekipleri dağıtmayı öğrenin.
ms.openlocfilehash: 053f92f0a3f7551d747c81b13b3832798c7e953c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63312604"
---
# <a name="configure-teams-with-protection-for-highly-sensitive-data"></a>Çok hassas veriler için ekipleri koruma ile yapılandırma

Bu makalede, çok hassas bir koruma düzeyi için ekip ayarlamayı istiyoruz. Bu makaledeki adımları uygulamadan önce, Ekipleri taban [çizgisi](configure-teams-baseline-protection.md) korumasıyla dağıtma makalesinde yer alan adımları tamamlamış olun.

Korumanın bu katmanı için, son derece hassas ekipler ve dosyalar için kuruluş genelinde kullanılmaktadır. Yalnızca belirttiğiniz kuruluş ve konuklarının bu etiketi kullanan dosyaların şifresini çözebilir. Yalnızca belirli bir ekibin üyelerinin dosya şifresini çözebilecekleri izinleri daha ayrıntılı olarak ayırmalısanız, bkz.  [Güvenlik yalıtlığı olan bir ekibi dağıtma](secure-teams-security-isolation.md).

Çok hassas katman, taban çizgisi katmanı üzerinde aşağıdaki ek korumaları sunar:

- Konuk paylaşımını açmanıza veya kapatmanıza ve kolay olmayan cihazlarda konuk içeriğine erişimi SharePoint ekip için duyarlılık etiketi. Bu etiket dosyaları sınıflandırmak ve şifrelemek için de kullanılabilir.
- Daha kısıtlayıcı bir varsayılan paylaşım bağlantı türü
- Yalnızca ekip sahipleri özel kanallar oluşturabilir.
- İlişkili site için erişim SharePoint istekleri kapalıdır.

## <a name="video-demonstration"></a>Video tanıtımı

Bu makalede açıklanan yordamları ayrıntılı olarak izlemek için bu videoyu izleyin.
<br>
<br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4NzI7]

## <a name="guest-sharing"></a>Konuk paylaşımı

İşletmenizin yapısına bağlı olarak, çok hassas veriler içeren ekipler için konuk paylaşımını etkinleştirmek istemeyebilirsiniz. Ekipte, kuruluş dışından kişilerle işbirliği yapmayı planlıyorsanız, konuk paylaşımını etkinleştirmenizi öneririz. Microsoft 365 hassas içeriği güvenli bir şekilde paylaşmanıza yardımcı olmak için çeşitli güvenlik ve uyumluluk özellikleri içerir. Bu genellikle, içeriği doğrudan kuruluş dışındakilere e-postayla göndermekten daha güvenli bir seçenektir.

Konuklarla güvenli bir şekilde paylaşma hakkında ayrıntılı bilgi için aşağıdaki kaynaklara bakın:

- [Kuruluş dışından kişilerle paylaşım sırasında dosyalarda yanlışlıkla açık kalma sürelerini sınırlama](./share-limit-accidental-exposure.md)
- [Güvenli bir konuk paylaşım ortamı oluşturma](./create-secure-guest-sharing-environment.md)

Konuk paylaşımına izin vermek veya engellemek için, her ikisi de daha sonra ele alınarak, ekip için bir duyarlılık etiketi ve ilişkili site SharePoint denetimlerini kullanırız.

## <a name="sensitivity-labels"></a>Duyarlılık etiketleri

Çok hassas bir koruma düzeyi için ekibi sınıflandırmak için bir duyarlılık etiketi kullan kullan istiyoruz. Bu etiket, bu ekiplerde veya diğer ekiplerde ya da özel ekipler veya ekip dosyaları gibi diğer dosya konumlarında tek tek dosyaları sınıflandırmak SharePoint OneDrive. 

İlk adım olarak, sizin için duyarlılık etiketlerini etkinleştirmeniz Teams. Ayrıntılar [için bkz. Microsoft Teams'ta, gruplarda Office 365 ve sitelerde SharePoint için duyarlılık etiketleri](../compliance/sensitivity-labels-teams-groups-sites.md) kullanma.

Zaten kuruluşta dağıtılmış duyarlılık etiketleriniz varsa, bu etiketin genel etiket stratejinize nasıl uyduğunu düşünün. Gerekirse, kuruluşun  ihtiyaçlarını karşılamak için adı veya ayarları değiştirebilirsiniz.

Daha sonra için duyarlılık etiketlerini etkinleştirdikten Teams, bir sonraki adım etiketi oluşturmaktır.

Duyarlılık etiketi oluşturmak için
1. Dosyayı [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com).
2. **Çözümler'in** altında Bilgi **koruma'ya tıklayın**.
3. Etiket **oluştur'a tıklayın**.
4. Etikete bir ad verme. Çok hassas **bir önerimiz** var, ancak bu ad zaten kullanıyorsa farklı bir ad seçebilirsiniz.
5. Bir görünen ad ve açıklama ekleyin ve ardından Sonraki'ye **tıklayın**.
6. Bu **etiketin kapsamını tanımla sayfasında** E-postalarda ve **Gruplarda & öğesini** **seçin ve &'a** **tıklayın**.
7. Dosyalar ve **e-postalar için koruma ayarlarını seçin sayfasında** Dosyaları ve e-postaları **şifrele'yi seçin** ve ardından Sonraki'ye **tıklayın**.
8. Şifreleme sayfasında **Şifreleme** ayarlarını **yapılandır'ı seçin**.
9. Belirli **kullanıcılara ve gruplara izin ata'nın altında** İzinleri **ata'ya tıklayın**.
10. **Kuruluşta tüm kullanıcıları ve grupları ekle'ye tıklayın**.
11. Dosyaların şifresini çözme izinleri olması gereken konuklar varsa, Kullanıcı veya grup **ekle'ye tıklayın ve** bunları ekleyin.
12.  **Kaydet'e** ve sonra da Sonraki'ne **tıklayın**.
13. Dosyalar ve *e-postalar için otomatik etiketleme** sayfasında, Sonraki'yi **tıklatın**.
14. Gruplar ve **siteler için koruma ayarlarını tanımla sayfasında** Gizlilik ve dış kullanıcı  erişimi ayarları ile Cihaz erişimi ve dış paylaşım ayarları'ı seçin ve **Ardından** Sonraki'ye **tıklayın**.
15. Gizlilik ve **dış kullanıcı erişimi ayarlarını tanımla sayfasında** , **Gizlilik'in altında** Özel **seçeneğini** belirtin.
16. Konuk erişimine izin vermek için Dış kullanıcı erişimi'nin altında **Grup** sahiplerinin Microsoft 365 dışından kişilerini gruba konuk olarak eklemesine **izin ver'i seçin**.
17. **İleri**'ye tıklayın.
18. Dış paylaşımı **ve cihaz erişim ayarlarını tanımla sayfasında, Site** etiketli **dış paylaşımı SharePoint seçin**.
19. Konuk **erişimine izin ediyorsanız** **İçerikle** paylaşılacak kişiler'in altında Yeni ve var olan konuklar'ı veya Bu seçeneğin altındaki **Yalnızca kuruluşta yer alan kişiler'i** seçin.
20. Kolay **olmayan cihazlardan erişim'in altında Erişimi** **engelle'yi seçin**. (Konukların yönetilen cihazlarına izin vermiyorsanız, Sınırlı, yalnızca web erişimine izin **ver'i seçebilirsiniz**.)
21. **İleri**'ye tıklayın.
22. Veritabanı **sütunları için otomatik etiketleme sayfasında, Sonraki'yi** **tıklatın**.
23. Etiket **oluştur'a** ve ardından **Bitti'ye tıklayın**.

Etiketi oluşturduktan sonra, bunu kullanacak kullanıcılara yayımlamanız gerekir. Hassas koruma için etiketi tüm kullanıcılarına kullandık. Etiketi, Bilgi koruma Microsoft 365 uyumluluk merkezi **Etiket ilkeleri sekmesinde yayımlarsiniz****.** Tüm kullanıcılar için geçerli olan bir ilkeniz varsa, bu etiketi bu ilkeye ekleyin. Yeni bir ilke oluşturmanız gerekirse, bkz. [Etiket ilkesi oluşturarak duyarlılık etiketlerini yayımlama](../compliance/create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy).

## <a name="create-a-team"></a>Ekip oluşturma

Üst düzeyde hassas senaryonun yapılandırmasını, ekiple SharePoint ilgili Site'de yapılır; bir sonraki adım ekip oluşturmaktır.

Çok hassas bilgiler için ekip oluşturmak
1. Ekip Teams, **uygulamanın Teams** tarafındaki Ekip Ekle'ye tıklayın ve ekip listesinin alt kısmından Takıma katıl  veya ekip oluştur'a tıklayın.
2. Ekip **oluştur'a** (ilk kart, sol üst köşede) tıklayın.
3. **Sıfırdan ekip oluşturma'yi seçin**.
4. Duyarlılık **listesinde,** az önce oluşturduğunuz **Çok hassas** etiketi seçin.
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

## <a name="sharepoint-settings"></a>SharePoint ayarları

Üst düzeyde hassas etikete sahip yeni bir ekip  oluşturmanıza yardımcı olacak iki SharePoint:

- Varsayılan paylaşım bağlantısını Varolan erişimi olan kişiler olarak güncelleştirmek SharePoint yönetim merkezinde sitenin konuk *paylaşım ayarlarını güncelleştirin*.
- Üyelerin dosyaları, klasörleri veya siteyi paylaşmalarını engellemek için sitenin kendi içinde site paylaşım ayarlarını güncelleştirin ve erişim isteklerini kapatın.

### <a name="site-default-sharing-link-settings"></a>Site varsayılan paylaşım bağlantısı ayarları

Site varsayılan paylaşım bağlantı türünü güncelleştirmek için

1. Site yönetim SharePoint açın ve **Siteler'in altında Etkin** <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**siteler'i seçin**</a>.
1. Ekiple ilişkilendirilmiş siteyi seçin.
1. **İlkeler sekmesindeki** Dış **paylaşım'ın altında** Düzenle'yi **seçin**.
1. Varsayılan paylaşım bağlantı türü'nin altında Kuruluş **düzeyi ayarıyla aynı onay kutusunu temizleyin** ve Varolan erişimi olan **kişiler'i seçin**.
1. **Kaydet**'i seçin.

#### <a name="private-channels"></a>Özel kanallar

Eklere özel kanallar eklersiniz, her özel kanal varsayılan paylaşım SharePoint yeni bir kanal sitesi oluşturur. Bu siteler SharePoint yönetim merkezinde görünmez, bu nedenle Set-SPOSite paylaşımı ayarlarını güncelleştirmek için Set-SPOSite PowerShell cmdlet'ini kullan gerekir.

### <a name="site-sharing-settings"></a>Site paylaşım ayarları

Sitenin, SharePoint üyesi değil kişileriyle paylaşılmaması için, bu paylaşımı sahiplerle sınırlandırdık. Ayrıca dosya ve klasörlerin paylaşımını ekip sahipleri ile de sınırlandırdık. Bu, ekip dışındaki biriyle paylaşılan dosyalarda sahiplerin farkında olmasını sağlamaya yardımcı olur.

Yalnızca sahipler için site paylaşımını yapılandırmak için
1. Güncelleştirme Teams, güncelleştirmek **istediğiniz** ekibin Genel sekmesine gidin.
2. Ekibin araç çubuğunda Dosyalar'a **tıklayın**.
3. Üç noktayı tıklatın ve sonra Üç **Nokta'da Aç'ı SharePoint**.
4. Temel sitenin araç çubuğunda SharePoint simgesine tıklayın ve sonra da Site **izinleri'ne tıklayın**.
5. Site izinleri **bölmesinde,** Site **paylaşımı'nın altında** Üyelerin **paylaşımlarını değiştir'e tıklayın**.
6. Paylaşım **izinleri'nin** **altında Yalnızca site sahipleri dosya, klasör ve siteyi paylaşabilir'i seçin**.
7. Erişim **isteklerine izin ver seçeneğini Kapalı** **olarak ayarlayın** ve Kaydet'e **tıklayın**.

## <a name="see-also"></a>Ayrıca Bkz

[Duyarlılık etiketlerini ve onların ilkelerini oluşturma ve yapılandırma](../compliance/create-sensitivity-labels.md)
