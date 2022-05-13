---
title: Benzersiz bir duyarlılık etiketi kullanarak ekibi güvenlik yalıtımıyla yapılandırma
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
- admindeeplinkSPO
recommendations: false
description: Güvenlik için benzersiz duyarlılık etiketine sahip bir ekip oluşturmayı öğrenin.
ms.openlocfilehash: 15f155255518df38921288f68dcc9365703e4f2a
ms.sourcegitcommit: 54bc063818779e351ca24f04ba571f762d85751d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2022
ms.locfileid: "65393120"
---
# <a name="configure-a-team-with-security-isolation-by-using-a-unique-sensitivity-label"></a>Benzersiz bir duyarlılık etiketi kullanarak ekibi güvenlik yalıtımıyla yapılandırma

Bu makalede, Microsoft Teams'da özel bir ekip yapılandırma ve dosyaları yalnızca ekip üyelerinin şifresini çözebilmesi için benzersiz bir duyarlılık etiketi kullanma önerileri ve adımları sağlanır.

Özel erişimin ötesinde, bu makalede, bir ekip kanalının **Dosyalar** bölümünden erişebileceğiniz ilişkili SharePoint sitesinin, yüksek düzeyde düzenlenmiş verileri depolamak için gereken ek güvenlik için nasıl yapılandırıldığı açıklanır.

Güvenlik yalıtımı olan bir ekip için yapılandırmanın öğeleri şunlardır:

- Özel bir ekip
- Ekip için ilişkili SharePoint sitesinde ek güvenlik:
  - Site üyelerinin siteyi başkalarıyla paylaşmasını engeller.
  - Site üyesi olmayanların siteye erişim istemesini engeller.
- Bu takıma özel olarak şu duyarlılık etiketi:
    - Yönetilmeyen cihazlardan SharePoint içeriğe erişimi engeller
    - Gereksinimlerinize bağlı olarak takıma konuk erişimine izin verir veya erişimi reddeder
    - Etiketin uygulandığı belgeleri şifreler

> [!IMPORTANT]
> Bu [makaledeki adımlara geçmeden önce Microsoft Teams, Office 365 grupları ve SharePoint sitelerdeki içeriği korumak için duyarlılık etiketlerini](../compliance/sensitivity-labels-teams-groups-sites.md) etkinleştirdiğinizden emin olun.

Dağıtım işlemine genel bir bakış için bu videoyu izleyin.
<br>
<br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4mGHf]

<a name="poster"></a>Bu senaryonun 1 sayfalık özeti için [güvenlik yalıtımlı Microsoft Teams posterini](../downloads/team-security-isolation-poster.pdf) inceleyin.

[![güvenlik yalıtım posteri ile Microsoft Teams.](../media/secure-teams-security-isolation/team-security-isolation-poster.png)](../downloads/team-security-isolation-poster.pdf)

Ayrıca bu posteri [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/team-security-isolation-poster.pdf) veya [PowerPoint](https://download.microsoft.com/download/8/0/5/8057fc16-c044-40b6-a652-7ed555ba2895/team-security-isolation-poster.pptx) biçimlerinde indirebilir ve mektup, yasal veya tabloid (11 x 17) boyutlu kağıda yazdırabilirsiniz.

Bu [yönergeleri](team-security-isolation-dev-test.md) kullanarak bu yapılandırmayı kendi test laboratuvarı ortamınızda deneyin.

Contoso Corporation'ın [bu örnek olay incelemesinde](contoso-team-for-top-secret-project.md) çok gizli bir proje için yalıtılmış bir ekibi nasıl kullandığını görün.

## <a name="initial-protections"></a>İlk korumalar

Takıma ve onun temel SharePoint sitesine erişimi korumaya yardımcı olmak için aşağıdaki en iyi yöntemleri gözden geçirin:
- [Kimlik ve cihaz erişim ilkeleri](../security/office-365-security/identity-access-policies.md)
- [çevrimiçi erişim ilkelerini SharePoint](../security/office-365-security/sharepoint-file-access-policies.md)
- [Temel koruma ile ekipleri dağıtma](configure-teams-baseline-protection.md)

## <a name="guest-sharing"></a>Konuk paylaşımı

İşletmenizin yapısına bağlı olarak, bu ekip için konuk paylaşımını etkinleştirmek isteyebilir veya istemeyebilirsiniz. Ekipte kuruluşunuzun dışındaki kişilerle işbirliği yapmayı planlıyorsanız konuk paylaşımını etkinleştirin. 

Konuklarla güvenli bir şekilde paylaşma hakkında ayrıntılı bilgi için aşağıdaki kaynaklara bakın:

- [Kuruluşunuzun dışındaki kişilerle paylaşım yaparken dosyaların yanlışlıkla açığa çıkmalarını sınırlayın](./share-limit-accidental-exposure.md)
- [Güvenli bir konuk paylaşım ortamı oluşturma](./create-secure-guest-sharing-environment.md)

Konuk paylaşımına izin vermek veya bunları engellemek için ekip için duyarlılık etiketinin ve ilişkili SharePoint sitesi için site düzeyinde paylaşım denetimlerinin bir bileşimini kullanırız. Her ikisi de daha sonra ele alınmalıdır.

## <a name="create-a-private-team"></a>Özel ekip oluşturma

Bu ekip için özel olarak bir duyarlılık etiketi oluşturduğumuz için bir sonraki adım ekibi oluşturmaktır. Mevcut bir ekibiniz varsa bunu kullanabilirsiniz.

Hassas bilgiler için ekip oluşturmak için
1. Teams'da, uygulamanın sol tarafındaki **Teams'e** tıklayın ve ardından ekip listesinin en altında **Katıl'a veya ekip oluştur'a** tıklayın.
2. **Ekip oluştur'a** tıklayın (ilk kart, sol üst köşe).
3. **Sıfırdan ekip oluştur'u** seçin.
4. **Duyarlılık** listesinde varsayılanı koruyun.
5. **Gizlilik'in** altında **Özel'e** tıklayın.
6. Takım için hassas projenizle ilgili bir ad yazın. Örneğin, **Satürn'Project**.
7. **Oluştur'a** tıklayın.
8. Takıma kullanıcı ekleyin ve **kapat'a** tıklayın.

## <a name="private-channel-settings"></a>Özel kanal ayarları

Özel kanal oluşturmayı ekip sahipleriyle kısıtlamanızı öneririz.

Özel kanal oluşturmayı kısıtlamak için
1. Ekipte **Diğer seçenekler'e** ve ardından **Ekibi yönet'e** tıklayın.
2. **Ayarlar** sekmesinde **Üye izinleri'ni** genişletin.
3. **Üyelerin özel kanal oluşturmasına izin ver** onay kutusunu temizleyin.

Özel kanal oluşturabilecekleri denetlemek için [teams ilkelerini](/MicrosoftTeams/teams-policies) de kullanabilirsiniz.

## <a name="create-a-sensitivity-label"></a>Duyarlılık etiketi oluşturma

Ekibi güvenlik yalıtımı için yapılandırmak için bu ekip için özel olarak oluşturulmuş bir duyarlılık etiketi kullanacağız. Bu etiket, konuk paylaşımını denetlemek ve yönetilmeyen cihazlardan erişimi engellemek için ekip düzeyinde kullanılır. Ayrıca yalnızca ekip sahiplerinin ve üyelerin açabilmesi için ekipteki tek tek dosyaları sınıflandırmak ve şifrelemek için de kullanılabilir.

Şifrelenmiş belgeleri görüntüleyebilmesi ancak düzenlememesi gereken bir iç iş ortağınız veya paydaş grubunuz varsa, bunları etikete yalnızca görüntüleme izinleriyle ekleyebilirsiniz. Daha sonra bu kişileri okuyucu izinleriyle ekibin SharePoint sitesine ekleyebilirsiniz. Bu kişiler, belgelerin tutulduğu siteye salt okunur erişime sahip olur ancak ekibin kendisine erişemez.

Duyarlılık etiketi oluşturmak için

1. Microsoft Purview uyumluluk portalı açın ve **Çözümler'in** altında <a href="https://go.microsoft.com/fwlink/p/?linkid=2174015" target="_blank">**Bilgi koruması'nı**</a> seçin.
1. **Etiket oluştur'a** tıklayın.
1. Etikete bir ad verin. Bunu birlikte kullandığınız ekipten sonra adlandırmanızı öneririz.
1. Bir görünen ad ve açıklama ekleyin ve **ardından İleri'ye** tıklayın.
1. **Bu etiket için kapsamı tanımla sayfasında****, E-postalar ve Gruplar &** **siteleri &** dosyalar'ı seçin ve **İleri'ye** tıklayın.
1. **Dosyalar ve e-postalar için koruma ayarlarını seçin** sayfasında **Dosyaları ve e-postaları şifrele'yi** seçin ve **ardından İleri'ye** tıklayın.
1. **Şifreleme** sayfasında **Şifreleme ayarlarını yapılandır'ı** seçin.
1. **Kullanıcı veya grup ekle'ye** tıklayın, oluşturduğunuz ekibi seçin ve **ekle'ye** tıklayın
1. **İzinleri seç'e** tıklayın.
1. Açılan **listeden Birlikte Yaz'ı** seçin ve **kaydet'e** tıklayın.
1. Etiketli dosyalara salt okunur erişimi olan kullanıcıları veya grupları dahil etmek istiyorsanız:
    1. **İzin ata'ya** tıklayın.
    1. **Kullanıcı veya grup ekle'ye** tıklayın, eklemek istediğiniz kullanıcıları veya grupları seçin ve **ekle'ye** tıklayın.
    1. **İzinleri seç'e** tıklayın.
    1. Açılan listeden **Görüntüleyici'yi** seçin ve **kaydet'e** tıklayın.
13.  **Kaydet'e** ve ardından **İleri'ye** tıklayın.
14. *Dosyalar ve e-postalar için otomatik etiketleme** sayfasında **İleri'ye** tıklayın.
15. **Gruplar ve siteler için koruma ayarlarını tanımla** sayfasında **Gizlilik ve dış kullanıcı erişim ayarları ile** **Cihaz erişimi ve dış paylaşım ayarları'nı seçin ve** **İleri'ye** tıklayın.
16. **Gizlilik ve dış kullanıcı erişimi ayarlarını tanımla** sayfasındaki **Gizlilik'in** altında **Özel** seçeneğini belirleyin.
17. Konuk erişimine izin vermek istiyorsanız **Dış kullanıcı erişimi'nin** altında **Grup sahiplerinin kuruluşunuz dışındaki kişileri gruba konuk olarak eklemesine izin Microsoft 365'ı** seçin.
18. **İleri**'ye tıklayın.
19. **Dış paylaşım ve cihaz erişim ayarlarını tanımla** sayfasında **Etiketli SharePoint sitelerden dış paylaşımı denetle'yi** seçin.
20. **İçerik paylaşılabilir** altında, konuk erişimine izin verirseniz **Yeni ve mevcut konuklar'ı** veya **Yalnızca kuruluşunuzdaki kişiler** (paylaşmıyorsanız) seçeneğini belirleyin.
21. **Yönetilmeyen cihazlardan erişim'in** altında **Erişimi engelle'yi** seçin.
22. **İleri**'ye tıklayın.
23. **Veritabanı sütunları için otomatik etiketleme** sayfasında **İleri'ye** tıklayın.
24. **Etiket oluştur'a** ve ardından **Bitti'ye** tıklayın.

Etiketi oluşturduktan sonra, etiketi kullanacak kullanıcılara yayımlamanız gerekir. Bu durumda etiketi yalnızca ekipteki kişilerin kullanımına sunacağız.

Duyarlılık etiketi yayımlamak için:

1. Microsoft Purview uyumluluk portalı <a href="https://go.microsoft.com/fwlink/p/?linkid=2174015" target="_blank">**, Bilgi koruma** sayfasında</a> **Etiket ilkeleri** sekmesini seçin.
2. **Etiketleri yayımla'ya** tıklayın.
3. **Yayımlamak için duyarlılık etiketlerini seçin sayfasında, Yayımlamak** **için duyarlılık etiketlerini seçin'e** tıklayın.
4. Oluşturduğunuz etiketi seçin ve **ekle'ye** tıklayın.
5. **İleri**'ye tıklayın.
6. Kullanıcılara ve gruplara yayımla sayfasında **Kullanıcıları ve grupları seç'e** tıklayın.
7. **Ekle'ye** tıklayın ve oluşturduğunuz ekibi seçin.
8. **Ekle'ye** ve ardından **Bitti'ye** tıklayın.
9. **İleri**'ye tıklayın.
10. İlke ayarları sayfasında, **Kullanıcılar bir etiketi veya daha düşük sınıflandırma etiketini kaldırmak için gerekçe sağlamalıdır** onay kutusunu seçin ve **ardından İleri'ye** tıklayın.
11. İlke için bir ad yazın ve **İleri'ye** tıklayın.
12. **Gönder'e** ve ardından **Bitti'ye** tıklayın.

## <a name="apply-the-label-to-the-team"></a>Etiketi takıma uygulama

Etiket yayımlandıktan sonra, konuk paylaşım ve yönetilen cihaz ayarlarının etkili olması için etiketi takıma uygulamanız gerekir. Bu işlem SharePoint yönetim merkezinde yapılır. Etiketin yayımlandıktan sonra kullanılabilir duruma gelmesi biraz zaman alabilir.

Duyarlılık etiketini uygulamak için

1. SharePoint yönetim merkezini açın ve **Siteler'in** altında <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Etkin siteler'i**</a> seçin.
1. Ekiple ilişkili siteyi seçin.
1. **İlkeler** sekmesindeki **Duyarlılık'ın** altında **Düzenle'yi** seçin.
1. Oluşturduğunuz etiketi seçin ve ardından **Kaydet'i** seçin.

## <a name="sharepoint-settings"></a>SharePoint ayarları

SharePoint'da yapılması gereken üç adım vardır:

- SharePoint yönetim merkezinde sitenin konuk paylaşım ayarlarını, etiketi oluştururken seçtiklerinizle eşleşecek şekilde güncelleştirin ve varsayılan paylaşım bağlantısını *Mevcut erişimi olan kişiler'e* güncelleştirin.
- Üyelerin dosya, klasör veya site paylaşmasını önlemek ve erişim isteklerini kapatmak için sitedeki site paylaşım ayarlarını güncelleştirin.
- Etikete Görüntüleyici izinleriyle kişi veya gruplar eklediyseniz, bunları Okuma izinleriyle SharePoint sitesine ekleyebilirsiniz.

### <a name="sharepoint-guest-settings"></a>Konuk ayarlarını SharePoint

Etiketi oluştururken seçtiğiniz konuk paylaşım ayarı (yalnızca ekip üyeliğini etkiler) aşağıdaki gibi ilişkili SharePoint sitesinin konuk paylaşım ayarlarıyla eşleşmelidir:

|Etiket ayarı|site ayarını SharePoint|
|:------------|:----------------------|
|**Office 365 grup sahiplerinin seçilen gruba kuruluş dışındaki kişileri eklemesine izin ver**|**Yeni ve mevcut konuklar** (yeni ekipler için varsayılan)|
|**Office 365 grup sahiplerinin seçili olmayan gruba kuruluş dışındaki kişileri eklemesine izin verin**|**Yalnızca kuruluşunuzdaki kişiler**|

Ayrıca, dosyaları ve klasörleri yanlışlıkla hedeflenenden daha geniş bir hedef kitleyle paylaşma riskini azaltmak için varsayılan paylaşım bağlantı türünü güncelleştireceğiz.

Site ayarlarını güncelleştirmek için

1. SharePoint yönetim merkezini açın ve **Siteler'in** altında <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Etkin siteler'i**</a> seçin
1. Ekiple ilişkili siteyi seçin.
1. **İlkeler** sekmesinde, **Dış paylaşım'ın** altında **Düzenle'yi** seçin.
1. Hassas etiketi oluştururken konuk paylaşımına izin verdiyseniz **Yeni ve mevcut konukların** seçili olduğundan emin olun. Etiketi oluştururken paylaşıma izin vermediyseniz **Yalnızca kuruluşunuzdaki kişiler'i** seçin.
1. Varsayılan paylaşım bağlantı türü'nün altında **Kuruluş düzeyi ayarıyla aynı** onay kutusunu temizleyin ve **Mevcut erişimi olan kişiler'i** seçin.
1. **Kaydet**'i seçin.

#### <a name="private-channels"></a>Özel kanallar

Takıma özel kanallar eklerseniz, her özel kanal varsayılan paylaşım ayarlarıyla yeni bir SharePoint sitesi oluşturur. Bu siteler SharePoint yönetim merkezinde görünmez, bu nedenle konuk paylaşım ayarlarını güncelleştirmek için [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) PowerShell cmdlet'ini aşağıdaki parametrelerle kullanmanız gerekir:

- `-SharingCapability Disabled` konuk paylaşımını kapatmak için (varsayılan olarak açıktır)
- `-DefaultSharingLinkType Internal`varsayılan paylaşım bağlantısını *Belirli kişiler* olarak değiştirmek için

Ekibinizle özel kanallar kullanmayı planlamıyorsanız, ekip üyelerinin ekip [ayarlarında](https://support.microsoft.com/office/ce053b04-1b8e-4796-baa8-90dc427b3acc) **Üye izinleri** altında bunları oluşturma yeteneğini kapatmayı göz önünde bulundurun.

### <a name="site-sharing-settings"></a>Site paylaşım ayarları

SharePoint sitesinin ekip üyesi olmayan kişilerle paylaşılmamasını sağlamaya yardımcı olmak için bu tür paylaşımları sahiplerle sınırlandırıyoruz. Ayrıca dosya ve klasörlerin paylaşımını ekip sahiplerine de sınırlandırıyoruz. Bu, ekip dışındaki biriyle her dosya paylaşıldığında sahiplerin farkında olmasını sağlamaya yardımcı olur.

Yalnızca sahipler için site paylaşımını yapılandırmak için
1. Teams'da güncelleştirmek istediğiniz ekibin **Genel** sekmesine gidin.
2. Ekibin araç çubuğunda **Dosyalar'a** tıklayın.
3. Üç noktaya tıklayın ve ardından **SharePoint aç'a** tıklayın.
4. Temel alınan SharePoint sitesinin araç çubuğunda ayarlar simgesine ve ardından **Site izinleri'ne** tıklayın.
5. Site izinleri bölmesinde, **Paylaşım Ayarlar** altında **Paylaşım ayarlarını değiştir'e** tıklayın.
6. **Paylaşım izinleri'nin** altında **Yalnızca site sahipleri dosyaları, klasörleri ve siteyi paylaşabilir'i seçin ve** **Kaydet'e** tıklayın.

### <a name="custom-site-permissions"></a>Özel site izinleri

Duyarlılık etiketine Görüntüleyici izinlerine sahip kişileri eklediyseniz, dosyalara kolayca erişebilmeleri için bunları Okuma erişimi ile SharePoint sitesine ekleyebilirsiniz.

Siteye kullanıcı eklemek için
1. Sitede ayarlar simgesine ve ardından **Site izinleri'ne** tıklayın.
2. **Kişileri davet et'e** ve ardından **Yalnızca siteyi paylaş'a** tıklayın.
3. Davet etmek istediğiniz kullanıcıların ve grupların adlarını yazın.
4. Eklediğiniz her kişi veya grup için, izinlerini **Düzenle** yerine **Okuma** olarak değiştirin.
5. Bu kişilere sitenin bağlantısını içeren bir e-posta göndermek isteyip istemediğinizi seçin.
6. **Ekle**'ye tıklayın.

## <a name="additional-protections"></a>Ek korumalar

Microsoft 365, içeriğinizin güvenliğini sağlamak için ek yöntemler sunar. Aşağıdaki seçeneklerin kuruluşunuzun güvenliğini artırmaya yardımcı olup olmadığını göz önünde bulundurun.

- Konuklarınızın [kullanım koşullarını kabul etmelerini](/azure/active-directory/conditional-access/terms-of-use) sağlayın.
- Konuklar için [oturum zaman aşımı ilkesi](/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime) yapılandırın.
- [Hassas bilgi türleri oluşturun ve hassas bilgilere](../compliance/sensitive-information-type-learn-about.md) erişimle ilgili ilkeler ayarlamak için [veri kaybı koruması](../compliance/dlp-learn-about-dlp.md) kullanın.
- Ekip erişimini ve üyeliğini düzenli aralıklarla gözden geçirmek için [Azure Active Directory erişim](/azure/active-directory/governance/access-reviews-overview) gözden geçirmelerini kullanın.

## <a name="drive-user-adoption-for-team-members"></a>Ekip üyeleri için kullanıcı benimsemesini yönlendirme

Ekip yerinde olduğunda, ekip üyelerine bu ekibin ve ek güvenliğinin benimsenmesinin zamanı geldi.

### <a name="train-your-users"></a>Kullanıcılarınızı eğitme

Ekibin üyeleri sohbetler, toplantılar ve diğer uygulamalar da dahil olmak üzere takıma ve tüm kaynaklarına erişebilir. Kanalın **Dosyalar** bölümünden dosyalarla çalışırken, ekip üyelerinin duyarlılık etiketini oluşturdukları dosyalara ataması gerekir.

Etiket dosyaya uygulandığında şifrelenir. Ekibin üyeleri bunu açabilir ve gerçek zamanlı olarak işbirliği yapabilir. Dosya siteden ayrılır ve kötü amaçlı bir kullanıcıya iletilirse, dosyayı açmak ve içeriğini görüntülemek için ekibin üyesi olan bir kullanıcı hesabının kimlik bilgilerini sağlaması gerekir. 

Ekip üyelerinizi eğitin:

- Yeni ekibi sohbetler, toplantılar, dosyalar ve SharePoint sitesinin diğer kaynakları için kullanmanın önemi ve yasal sonuçlar, yasal cezalar, fidye yazılımı veya rekabet avantajı kaybı gibi yüksek düzeyde düzenlenmiş bir veri sızıntısının sonuçları.
- Takıma erişme.
- Sitede yeni dosyalar oluşturma ve yerel olarak depolanan yeni dosyaları karşıya yükleme.
- Takım için dosyaları doğru duyarlılık etiketiyle etiketleme.
- Etiket, siteden sızdırıldığında bile dosyaları nasıl korur?

Bu eğitim, ekip üyelerinizin bu özellikleri ve sonuçlarını deneyimleyebilmesi için uygulamalı alıştırmalar içermelidir.

### <a name="conduct-periodic-reviews-of-usage-and-address-team-member-feedback"></a>Kullanımla ilgili düzenli incelemeler yapma ve ekip üyesi geri bildirimlerini ele alma

Eğitimden sonraki haftalarda:

- Ekip üyesi geri bildirimlerini hızla ele alın ve ilkeler ile yapılandırmalar için ince ayar yapın.
- Ekip için kullanımı analiz edin ve kullanım beklentileriyle karşılaştırın.
- Yüksek oranda düzenlenmiş dosyaların duyarlılık etiketiyle düzgün şekilde etiketlendiğini doğrulayın. (SharePoint'da bir klasörü görüntüleyerek ve **Sütun** **ekle'nin** **Sütunları göster/gizle** seçeneği aracılığıyla Duyarlılık sütununu ekleyerek hangi dosyaların atanmış olduğunu görebilirsiniz.

Kullanıcılarınızı gerektiği gibi yeniden eğitin.

## <a name="see-also"></a>Ayrıca bkz.

[Azure AD Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-configure)
