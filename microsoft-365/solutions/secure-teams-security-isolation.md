---
title: Ekibi güvenlik yalıtlığı ile yapılandırma
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-3tiersprotection
- m365solution-securecollab
ms.custom:
- Ent_Solutions
- admindeeplinkCOMPLIANCE
recommendations: false
description: Güvenlik için benzersiz bir duyarlılık etiketi olan bir ekip oluşturma hakkında bilgi öğrenin.
ms.openlocfilehash: 293ac9a1a28757dacba39d30e619ac41be786e04
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990586"
---
# <a name="configure-a-team-with-security-isolation"></a>Ekibi güvenlik yalıtlığı ile yapılandırma

Bu makale size, Microsoft Teams'de özel bir ekibi yapılandırma ve dosyaların şifresini yalnızca ekip üyelerinin çözebilecekleri şekilde dosyaları şifrelemek için benzersiz bir duyarlılık etiketi kullanma önerileri ve adımları sağlar.

Özel erişim dışında, bu makalede, son derece düzenlemeye tabi verileri depolamak için gereken ek güvenlik için ekip kanalının Dosyalar bölümünden erişebilirsiniz  olan ilişkili SharePoint sitesini nasıl yapılandırabilirsiniz? açıklanmıştır.

Güvenlik yalıtlığı olan bir ekibin yapılandırma öğeleri:

- Özel ekip
- Ek güvenlik SharePoint ekip için:
  - Site üyelerinin siteyi başkalarıyla paylaşmasını engelleme.
  - Sitenin üyesi olmayanların siteye erişim isteğiyle ilgili istekte bulunanlarını önler.
- Şu ekip için özel olarak bir duyarlılık etiketi:
    - İçeriğin, SharePoint cihazlara erişimini engellemektedir
    - Gereksinimlerinize bağlı olarak, konuk ekibine konuk erişimine izin verir veya bu erişimin izinlerini geri ister
    - Etiketin uygulandığı belgeleri şifreler

> [!IMPORTANT]
> Bu makaledeki adımlarla [devammeden önce Microsoft Teams, Office 365](../compliance/sensitivity-labels-teams-groups-sites.md) grupları ve SharePoint sitelerinin içeriğini korumak için duyarlılık etiketlerini etkinleştirmiş olun.

Dağıtım sürecine genel bir bakış için bu videoyu izleyin.
<br>
<br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4mGHf]

<a name="poster"></a>Bu senaryonun 1 sayfalık bir özeti için güvenlik Microsoft Teams [posteri ile ilgili özete bakın](../downloads/team-security-isolation-poster.pdf).

[![Microsoft Teams yalıtım posteri ile bir poster.](../media/secure-teams-security-isolation/team-security-isolation-poster.png)](../downloads/team-security-isolation-poster.pdf)

Ayrıca bu posteri [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/team-security-isolation-poster.pdf) veya tablo PowerPoint ve [](https://download.microsoft.com/download/8/0/5/8057fc16-c044-40b6-a652-7ed555ba2895/team-security-isolation-poster.pptx) letter, legal veya tabloid (11 x 17) boyutlu kağıda yazdırabilirsiniz.

Bu yönergeleri izleyerek bu yapılandırmayı kendi test laboratuvarı [ortamınıza deneyin](team-security-isolation-dev-test.md).

Bu örnek olay incelemesinde Contoso Corporation'ın çok gizli bir proje için nasıl yalıtılmış [bir ekibi nasıl kullandığına bakın](contoso-team-for-top-secret-project.md).

## <a name="initial-protections"></a>İlk korumalar

Takıma ve ekibin temel özelliklerine erişimin korunmasına yardımcı SharePoint, aşağıdaki en iyi yöntemleri gözden geçirin:
- [Kimlik ve cihaz erişim ilkeleri](../security/office-365-security/identity-access-policies.md)
- [SharePoint Online erişim ilkeleri](../security/office-365-security/sharepoint-file-access-policies.md)
- [Taban çizgisi korumasıyla ekipleri dağıtma](configure-teams-baseline-protection.md)

## <a name="guest-sharing"></a>Konuk paylaşımı

İşletmenizin yapısına bağlı olarak, bu ekipte konuk paylaşımını etkinleştirmek istiyor veya etmek istemiyor olabilirsiniz. Ekipte, kuruluş dışından kişilerle işbirliği yapmayı planlıyorsanız, konuk paylaşımını etkinleştirin. 

Konuklarla güvenli bir şekilde paylaşma hakkında ayrıntılı bilgi için aşağıdaki kaynaklara bakın:

- [Kuruluş dışından kişilerle paylaşım sırasında dosyalarda yanlışlıkla açık kalma sürelerini sınırlama](./share-limit-accidental-exposure.md)
- [Güvenli bir konuk paylaşım ortamı oluşturma](./create-secure-guest-sharing-environment.md)

Konuk paylaşımına izin vermek veya engellemek için, her ikisi de daha sonra ele alınarak, ekip için bir duyarlılık etiketi ve ilişkili site SharePoint denetimlerini kullanırız.

## <a name="create-a-private-team"></a>Özel ekip oluşturma

Bu ekip için özel olarak bir duyarlılık etiketi oluşturduktan sonra bir sonraki adım ekibi oluşturmaktır. Mevcut bir takımınız varsa bunu kullanabilirsiniz.

Hassas bilgiler için ekip oluşturmak için
1. Ekip Teams, **uygulamanın Teams** tarafındaki Ekip Ekle'ye tıklayın ve ekip listesinin alt kısmından Takıma katıl  veya ekip oluştur'a tıklayın.
2. Ekip **oluştur'a** (ilk kart, sol üst köşede) tıklayın.
3. **Sıfırdan ekip oluşturma'yi seçin**.
4. Duyarlılık **listesinde varsayılanı** kullanın.
5. **Gizlilik'in** altında **Özel'e tıklayın**.
6. Hassas projeniz ile ilgili ekip için bir ad yazın. Örneğin, **Satürn Project.**
7. **Oluştur'a tıklayın**.
8. Ekseta kullanıcı ekleyin ve Kapat'a **tıklayın**.

## <a name="private-channel-settings"></a>Özel kanal ayarları

Özel kanallar oluşturmayı ekip sahipleri ile kısıtlamayı öneririz.

Özel kanal oluşturma kısıtlamak için
1. Ekipte Diğer **seçenekler'e ve sonra** da Ekibi yönet'e **tıklayın**.
2. Ekle **Ayarlar** Üye **izinleri'ne tıklayın**.
3. Üyelerin **özel kanal oluşturmasına izin ver onay** kutusunu temizleyin.

Ayrıca, kimlerin özel [kanal oluştura](/MicrosoftTeams/teams-policies) onu kontrol etmek için ekip ilkelerini de kullanabilirsiniz.

## <a name="create-a-sensitivity-label"></a>Duyarlılık etiketi oluşturma

Bir ekibi güvenlik yalıtması için yapılandırmak üzere bu ekip için özel olarak oluşturulmuş bir duyarlılık etiketi kullan ayarlarız. Bu etiket, konuk paylaşımını kontrol etmek ve kontrolü olmayan cihazlara erişimi engellemek için ekip düzeyinde kullanılır. Ayrıca, yalnızca ekip sahipleri ve üyeleri tarafından açılmaları için ekipte tek tek dosyaları sınıflandırmak ve şifrelemek için de kullanılabilir.

Şifreli belgeleri görüntüley düzenlemeleri gerektir gereken ancak düzenley kayıtta olmayan bir iç iş ortağınız veya proje katılımcı grubunuz varsa, bunları yalnızca görüntüleme izinleri olan etikete  eklersiniz. Böylece, bu kişiler Okuyucu izinleriyle SharePoint ekip sitesi'ne  eklersiniz ve belgelerin tutul olduğu siteye salt okunur erişimleri olur; bunlar ekibin kendisinin değil.

Duyarlılık etiketi oluşturmak için

1. Çalışma Microsoft 365 uyumluluk merkezi Çözümler'in **altında Bilgi** <a href="https://go.microsoft.com/fwlink/p/?linkid=2174015" target="_blank">**koruması'ı seçin**</a>.
1. Etiket **oluştur'a tıklayın**.
1. Etikete bir ad verme. Birlikte kullanmakta olacağınız ekibin adını ekip olarak adlandırmanızı öneririz.
1. Bir görünen ad ve açıklama ekleyin ve ardından Sonraki'ye **tıklayın**.
1. Bu **etiketin kapsamını tanımla sayfasında** E-postalarda ve **Gruplarda & öğesini** **seçin ve &'a** **tıklayın**.
1. Dosyalar ve **e-postalar için koruma ayarlarını seçin sayfasında** Dosyaları ve e-postaları **şifrele'yi seçin** ve ardından Sonraki'ye **tıklayın**.
1. Şifreleme sayfasında **Şifreleme** ayarlarını **yapılandır'ı seçin**.
1. Kullanıcı **veya grup ekle'ye** tıklayın, oluşturduğunuz ekibi seçin ve Ekle'ye **tıklayın**
1. İzinleri **seç'e tıklayın**.
1. Açılan **listeden Ortak Yazar'ı** seçin ve ardından Kaydet'e **tıklayın**.
1. Etiketli dosyalara salt okunur erişimi olan kullanıcıları veya grupları dahil etmek için:
    1. İzinleri **ata'ya tıklayın**.
    1. Kullanıcı **veya grup ekle'ye** tıklayın, eklemek istediğiniz kullanıcıları veya grupları seçin ve Ekle'ye **tıklayın**.
    1. İzinleri **seç'e tıklayın**.
    1. Açılan **listeden** Görüntüleyici'yi seçin ve ardından Kaydet'e **tıklayın**.
13.  **Kaydet'e** ve sonra da Sonraki'ne **tıklayın**.
14. Dosyalar ve *e-postalar için otomatik etiketleme** sayfasında, Sonraki'yi **tıklatın**.
15. Gruplar ve **siteler için koruma ayarlarını tanımla sayfasında** Gizlilik ve dış kullanıcı  erişimi ayarları ile Cihaz erişimi ve dış paylaşım ayarları'ı seçin ve **Ardından** Sonraki'ye **tıklayın**.
16. Gizlilik ve **dış kullanıcı erişimi ayarlarını tanımla sayfasında** , **Gizlilik'in altında** Özel **seçeneğini** belirtin.
17. Konuk erişimine izin vermek için Dış kullanıcı erişimi'nin altında **Grup** sahiplerinin Microsoft 365 dışından kişilerini gruba konuk olarak eklemesine **izin ver'i seçin**.
18. **İleri**'ye tıklayın.
19. Dış paylaşımı **ve cihaz erişim ayarlarını tanımla sayfasında, Site** etiketli **dış paylaşımı SharePoint seçin**.
20. Konuk **erişimine izin ediyorsanız** **İçerikle** paylaşılacak kişiler'in altında Yeni ve var olan konuklar'ı veya Bu seçeneğin altındaki **Yalnızca kuruluşta yer alan kişiler'i** seçin.
21. Kolay **olmayan cihazlardan erişim'in altında Erişimi** **engelle'yi seçin**.
22. **İleri**'ye tıklayın.
23. Veritabanı **sütunları için otomatik etiketleme sayfasında, Sonraki'yi** **tıklatın**.
24. Etiket **oluştur'a** ve ardından **Bitti'ye tıklayın**.

Etiketi oluşturduktan sonra, bunu kullanacak kullanıcılara yayımlamanız gerekir. Bu durumda, etiketi yalnızca ekipte yer alan kişiler için kullanılabilir hale biz ekleriz.

Duyarlılık etiketini yayımlamak için:

1. Etiket Microsoft 365 uyumluluk merkezi, <a href="https://go.microsoft.com/fwlink/p/?linkid=2174015" target="_blank">**Bilgi koruması** sayfasında</a> Etiket ilkeleri **sekmesini** seçin.
2. Etiketleri **yayımla'ya tıklayın**.
3. Yayımlayacak **duyarlılık etiketlerini seçin sayfasında** Yayımlayacak duyarlılık **etiketlerini seç'e tıklayın**.
4. Oluşturduğunuz etiketi seçin ve Ekle'ye **tıklayın**.
5. **İleri**'ye tıklayın.
6. Kullanıcılar ve gruplara yayımla sayfasında Kullanıcıları ve **grupları seç'e tıklayın**.
7. **Ekle'ye** tıklayın ve oluşturduğunuz ekibi seçin.
8. **Ekle'ye** ve ardından **Bitti'ye tıklayın**.
9. **İleri**'ye tıklayın.
10. İlke ayarları sayfasında, Kullanıcılar bir etiketi **veya daha düşük** bir sınıflandırma etiketini kaldırmak için gerekçe sağlamalı onay kutusunu seçin ve sonra da Sonraki'ye **tıklayın**.
11. İlke için bir ad yazın ve Ardından Sonraki'ye **tıklayın**.
12. **Gönder'e** ve ardından **Bitti'ye tıklayın**.

## <a name="apply-the-label-to-the-team"></a>Etiketi takıma uygulama

Etiket yayımlandıktan sonra, konuk paylaşımının ve yönetilen cihaz ayarlarının etkili olması için etiketi bir ekiple birlikte uygulamanız gerekir. Bu, SharePoint merkezinde yapılır. Etiket yayımlandıktan sonra kullanılabilir olması biraz zaman alsa da bunu unutmayın.

Duyarlılık etiketini uygulamak için
1. SharePoint [merkezini açın](https://admin.microsoft.com/sharepoint).
2. **Siteler'in** altında Etkin **siteler'e tıklayın**.
3. Ekiple ilişkilendirilmiş siteye tıklayın.
4. **İlkeler sekmesindeki** **Duyarlılık'ın altında** Düzenle'ye **tıklayın**.
5. Oluşturduğunuz etiketi seçin ve kaydet'e **tıklayın**.

## <a name="sharepoint-settings"></a>SharePoint ayarları

Bu adımda üç SharePoint:

- SharePoint yönetim merkezinde sitenin konuk paylaşım ayarlarını, etiketi oluşturulduğunda seçtiğiniz etiketle eş olacak şekilde güncelleştirin ve varsayılan paylaşım bağlantısını Varolan erişimi olan *kişiler'e güncelleştirin*.
- Üyelerin dosyaları, klasörleri veya siteyi paylaşmalarını engellemek için sitenin kendi içinde site paylaşım ayarlarını güncelleştirin ve erişim isteklerini kapatın.
- Görüntüleyici izinleri olan etikete kişi veya gruplar eklediysanız, bunları Okuma izinlerine sahip SharePoint Site'ye ebilirsiniz.

### <a name="sharepoint-guest-settings"></a>SharePoint ayarlarını değiştirme

Etiketi oluşturulduğunda seçtiğiniz konuk paylaşım ayarı (yalnızca ekip üyeliğini etkiler) ilişkili etki alanı sitenin konuk paylaşım ayarlarıyla aşağıdaki SharePoint eşleşmesi gerekir:

|Etiket ayarı|SharePoint sitesi ayarı|
|:------------|:----------------------|
|**Grup Office 365 seçilen gruba kuruluş dışındaki kişilerin de kişi eklemesine izin** verme|**Yeni ve mevcut konuklar** (yeni ekipler için varsayılan)|
|**Grup Office 365 seçilen gruba kuruluş dışından kişi eklemesine** izin verme|**Yalnızca kuruluşta yer alan kişiler**|

Ayrıca, dosya ve klasörleri yanlışlıkla hedeflenenden daha geniş bir hedef kitleye paylaşma riskini azaltmak için varsayılan paylaşım bağlantı türünü güncelleştirecektir.

Site ayarlarını güncelleştirmek için
1. SharePoint [merkezini açın](https://admin.microsoft.com/sharepoint).
2. **Siteler'in** altında Etkin **siteler'e tıklayın**.
3. Ekiple ilişkilendirilmiş siteye tıklayın.
4. **İlkeler sekmesinde**, Dış **paylaşım'ın altında** Düzenle'ye **tıklayın**.
5. Hassas etiketi oluşturulduğunda konuk paylaşımına izin verdiysanız Yeni ve mevcut **konuklar'ın seçili olduğundan** emin olun. Etiketi oluşturulduğunda paylaşıma izin vermediysiniz, Yalnızca **kuruluşta yer alan kişiler'i seçin**.
6. Varsayılan paylaşım bağlantı türü'nin altında Kuruluş **düzeyi ayarıyla aynı onay kutusunu temizleyin** ve Varolan erişimi olan **kişiler'i seçin**.
7. **Kaydet**'e tıklayın.

#### <a name="private-channels"></a>Özel kanallar

Eklere özel kanallar eklersiniz, her özel kanal varsayılan paylaşım SharePoint yeni bir kanal sitesi oluşturur. Bu siteler SharePoint yönetim merkezinde görünmez, bu nedenle konuk paylaşım ayarlarını güncelleştirmek için [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) PowerShell cmdlet'ini aşağıdaki parametrelerle kullan gerekir:

- `-SharingCapability Disabled` konuk paylaşımını kapatmak için (varsayılan olarak açıktır)
- `-DefaultSharingLinkType Internal` varsayılan paylaşım bağlantısını Belirli kişiler *olarak değiştirmek için*

Takımınız için özel kanallar kullanmayı planlamıyorsanız, ekip üyelerinin ekip ayarlarında Üye izinleri altında kanal oluşturma yeteneğini [kapatmayı düşünebilirsiniz](https://support.microsoft.com/office/ce053b04-1b8e-4796-baa8-90dc427b3acc).

### <a name="site-sharing-settings"></a>Site paylaşım ayarları

Sitenin, SharePoint üyesi değil kişileriyle paylaşılmaması için, bu paylaşımı sahiplerle sınırlandırdık. Ayrıca dosya ve klasörlerin paylaşımını ekip sahipleri ile de sınırlandırdık. Bu, ekip dışındaki biriyle paylaşılan dosyalarda sahiplerin farkında olmasını sağlamaya yardımcı olur.

Yalnızca sahipler için site paylaşımını yapılandırmak için
1. Güncelleştirme Teams, güncelleştirmek **istediğiniz** ekibin Genel sekmesine gidin.
2. Ekibin araç çubuğunda Dosyalar'a **tıklayın**.
3. Üç noktayı tıklatın ve sonra Üç **Nokta'da Aç'ı SharePoint**.
4. Temel sitenin araç çubuğunda SharePoint simgesine tıklayın ve sonra da Site **izinleri'ne tıklayın**.
5. Site izinleri bölmesinde, Paylaşım **Ayarları'nın Ayarlar** Ayarları **değiştir'e tıklayın**.
6. Paylaşım **izinleri'nin** **altında Yalnızca site sahipleri dosyaları, klasörleri ve siteyi** paylaşabilir'i seçin ve Kaydet'e **tıklayın**.

### <a name="custom-site-permissions"></a>Özel site izinleri

Duyarlılık etiketine Görüntüleyici izinleri olan kişiler eklediysanız, dosyalara kolay erişimleri için bunları Okuma erişimi SharePoint sitenize  eklersiniz.

Siteye kullanıcı eklemek için
1. Sitede, ayarlar simgesine ve sonra Site **izinleri'ne tıklayın**.
2. Kişileri **davet et'e** ve ardından Yalnızca **siteyi paylaş'a tıklayın**.
3. Davet etmek istediğiniz kullanıcıların ve grupların adlarını yazın.
4. Ekley istediğiniz her kişi veya grup için düzenle olan izinlerini Okuma **olarak** **değiştirebilirsiniz**.
5. Siteye bağlantı içeren bir e-posta göndermek mi istediğinize tıklayın.
6. **Ekle**'ye tıklayın.

## <a name="additional-protections"></a>Ek korumalar

Microsoft 365, içeriğinizin güvenliğini sağlamak için ek yöntemler sunar. Aşağıdaki seçeneklerin, organizasyon güvenliğinizi iyileştirmeye yardımcı olup olacağını düşünün.

- Konuklardan kullanım koşullarını kabul [göstermelerini s anlayabilirler](/azure/active-directory/conditional-access/terms-of-use).
- Konuklar için [oturum zaman aşımı ilkesi](/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime) yapılandırma.
- Hassas [bilgi türleri oluşturun ve](../compliance/sensitive-information-type-learn-about.md) hassas bilgilere [erişimle ilgili](../compliance/dlp-learn-about-dlp.md) ilkeler ayarlamak için veri kaybına karşı koruma kullanın.
- Ekip [erişimini Azure Active Directory üyelikleri](/azure/active-directory/governance/access-reviews-overview) düzenli olarak gözden geçirmek için incelemelere erişmek için incelemeleri kullanın.

## <a name="drive-user-adoption-for-team-members"></a>Ekip üyeleri için kullanıcının benimsemesine yol verme

Ekip yerine bulundurarak, şimdi bu ekibin benimsenme ve ekip üyelerine ek güvenlik vermenin zamanı geldi.

### <a name="train-your-users"></a>Kullanıcılarınızı eğitme

Ekip üyeleri, sohbetler, toplantılar ve diğer uygulamalar da dahil ekibin tüm kaynaklarına erişim sağlar. Kanalın Dosyalar bölümünden **dosyalarla** çalışırken, ekip üyelerinin oluşturdukları dosyalara duyarlılık etiketini atamaları gerekir.

Etiket dosyaya uygulandığında, şifrelenir. Ekip üyeleri dosyayı açabilir ve gerçek zamanlı olarak işbirliği yaptıklarında. Dosya siteden ayrılır ve kötü amaçlı bir kullanıcıya ilet istenirse, dosyayı açmak ve içeriğini görüntülemek için ekibin üyesi olan bir kullanıcı hesabının kimlik bilgilerini sağlamak zorunda olur. 

Ekip üyelerinizi eğitin:

- Yeni ekibi SharePoint sitesinde sohbetler, toplantılar, dosyalar ve diğer kaynaklar için kullanmanın önemi ve yasal büyütme, mevzuatla ilgili hassas düzenlemeler, fidye yazılımı veya rekabetçi avantajın kaybı gibi son derece düzenlemeye tabi veri sızıntılarının sonuçları.
- Ekiplere erişim.
- Sitede yeni dosyalar oluşturma ve yerel olarak depolanan yeni dosyaları karşıya yükleme.
- Dosyaları ekip için doğru duyarlılık etiketiyle etiketleme.
- Etiket, siteden sızdırılmış olsa bile dosyaları nasıl korur.

Bu eğitim, ekip üyelerinizin bu özellikleri ve sonuçlarını elde etmek için uygulamalı alıştırmalar içermesi gerekir.

### <a name="conduct-periodic-reviews-of-usage-and-address-team-member-feedback"></a>Düzenli olarak kullanım incelemeleri gerçekleştirin ve ekip üyesi geri bildirimlerini gönderin

Eğitimden sonra haftalar içinde:

- Ekip üyesi geri bildirimlerine hızlıca adres yazın, güvenlik bildirimlerini ve yapılandırmaları ince ayarlayın.
- Ekibin kullanımını analiz edin ve bunu kullanım beklentileriyle karşılaştırın.
- Yüksek düzeyde düzenlemeye tabi dosyaların duyarlılık etiketiyle düzgün bir şekilde etiketlenmiş olduğunu doğrulayın. (Farklı SharePoint bir klasörde bir klasörü görüntüerek ve Sütun ekle'nin Sütunları göster **/** gizle seçeneği aracılığıyla Duyarlılık sütununu  ekleyerek hangi dosyalara bir etiket **atandığıyla ilgili bilgi edinebilirsiniz**.

Kullanıcılarınızı gereken şekilde yeniden kısıtlayın.

## <a name="see-also"></a>Ayrıca bkz.

[Azure AD Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-configure)