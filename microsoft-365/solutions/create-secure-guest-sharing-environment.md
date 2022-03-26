---
title: Güvenli bir konuk paylaşım ortamı oluşturma
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-security-compliance
- m365solution-3tiersprotection
- m365solution-securecollab
- m365initiative-externalcollab
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.localizationpriority: high
f1.keywords: NOCSH
recommendations: false
description: İş birliği geliştirmek için konuk erişimi sağlamak ve bu ortamda güvenli bir Microsoft 365 için kullanılabilir seçenekler hakkında bilgi öğrenin.
ms.openlocfilehash: 13190f2dba0f2cb1f4817a1a831b8d78359e1b81
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2022
ms.locfileid: "63715151"
---
# <a name="create-a-secure-guest-sharing-environment"></a>Güvenli bir konuk paylaşım ortamı oluşturma

Bu makalede, iş yeriz için güvenlikli bir konuk paylaşım ortamı oluşturmak üzere çeşitli seçenekler Microsoft 365. Bunlar, size kullanılabilir seçenekler hakkında fikir vermeyle ilgili örneklerdir. Bu yordamları, kuruma ilişkin güvenlik ve uyumluluk  gereklerini karşılamak için farklı birleşimlerde kullanabilirsiniz.

Bu makale şunları içerir:

- Konuklar için çok faktörlü kimlik doğrulamasını ayarlama.
- Konuklar için kullanım koşullarını ayarlama.
- Konukların ekipler ve siteler için izinlere ihtiyaç olup olmadığını düzenli aralıklarla doğrulamak için üç aylık konuk erişimi incelemelerini ayarlama.
- Konukları, yalnızca web erişimiyle, unmanaged cihazları için kısıtlama.
- Konukların günlük kimlik doğrulamasını sağlamak için oturum zaman aşımı ilkesi yapılandırma.
- Çok hassas bir proje için hassas bir bilgi türü oluşturma.
- Hassas bir bilgi türü içeren belgelere otomatik olarak duyarlılık etiketi atama.
- Duyarlılık etiketi olan dosyalardan konuk erişimini otomatik olarak kaldırabilirsiniz.

Bu makalede tartışılan seçeneklerden bazıları, konukların posta kutusunda bir hesabı Azure Active Directory. Dosyaları ve klasörleri onlarla paylaşırken konukların da dizine dahil olduğundan emin olmak için Azure [AD B2B Preview ile SharePoint OneDrive tümleştirmesini kullanın](/sharepoint/sharepoint-azureb2b-integration-preview).

Bu makalede konuk paylaşımı ayarlarını etkinleştirme konusunu tartışmayacağız. Farklı [senaryolarda konuk paylaşımını etkinleştirme hakkında ayrıntılı](collaborate-with-people-outside-your-organization.md) bilgi için bkz. Kuruluş dışındaki kişiler ile işbirliği.

## <a name="set-up-multi-factor-authentication-for-guests"></a>Konuklar için çok faktörlü kimlik doğrulamasını ayarlama

Çok faktörlü kimlik doğrulaması, bir hesabın tehlikeye atılmış olma riskini büyük ölçüde azaltır. Konuklar herhangi bir yönetim ilkelerine veya en iyi uygulamalara uymayen kişisel e-posta hesapları kullanıyor olabilir, bu nedenle konuklar için çok faktörlü kimlik doğrulaması gerektirmeniz özellikle önemlidir. Bir konuğun kullanıcı adı ve parolası çalınırsa, kimlik doğrulamasının ikinci bir faktöre sahip olmak, bilinmeyen tarafların site ve dosyalarınıza erişim kazanmasını büyük ölçüde azaltır.

Bu örnekte, konukların çok faktörlü kimlik doğrulamasını ayarlamak için, Azure Active Directory.

Konuklar için çok faktörlü kimlik doğrulamasını ayarlamak için

1. Azure koşullu [erişim ilkeleri'ne gidin](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade).
2. Koşullu **Erişim | İlkeler** blade, Yeni **ilke'ye tıklayın**.
3. Ad **alanına** bir ad yazın.
4. **Atamalar'ın** altında Kullanıcılar **ve gruplar'a tıklayın**.
5. Kullanıcılar ve **gruplar blade'inde** Kullanıcıları **ve grupları seç'i**, ardından **Tüm konuklar ve dış kullanıcılar onay kutusunu** seçin.
6. **Atamalar'ın altında** Bulut **uygulamaları veya eylemleri'ne tıklayın**.
7. Bulut uygulamaları **veya eylemler blade'inde** Ekle **sekmesinde Tüm bulut** **uygulamaları'ı** seçin.
8. Erişim **denetimleri'nin altında** **Ver'e tıklayın**.
9. Blade **ver'de** Çok faktörlü **kimlik doğrulaması gerektir onay kutusunu** seçin ve ardından Seç'e **tıklayın**.
10. Yeni **blade'de** , **İlkeyi etkinleştir'in altında** **Etkin'e tıklayın** ve sonra da Oluştur'a **tıklayın**.

Artık konuğun paylaşılan içeriğe, sitelere veya ekiplere erişmeden önce çok faktörlü kimlik doğrulamasına kaydolması gerekiyor.

### <a name="more-information"></a>Daha fazla bilgi

[Azure AD çok faktörlü kimlik doğrulama dağıtımını planlama](/azure/active-directory/authentication/howto-mfa-getstarted)

## <a name="set-up-a-terms-of-use-for-guests"></a>Konuklar için kullanım koşulları ayarlama

Bazı durumlarda konuklar, gizlilik sözleşmesi veya organizasyonla başka yasal sözleşmeler imzalamış olabilir. Konukların, onlarla paylaşılan dosyalara erişmeden önce bir kullanım koşullarını kabul etmiş göstermelerini gerekli bulundurabilirsiniz. Paylaşılan bir dosya veya siteye ilk kez erişmeye çalışan kullanım koşulları görüntülenebilir.

Kullanım koşulları oluşturmak için, önce Word'de veya başka bir yazma programında belgeyi oluşturmanız ve sonra bunu bir .pdf kaydetmeniz gerekir. Bu dosya daha sonra Azure AD'ye yüklenebilirsiniz.

Azure AD kullanım koşulları oluşturmak için

1. Genel Yönetici, Güvenlik Yöneticisi veya Koşullu Erişim Yöneticisi olarak Azure'da oturum açın.
2. Kullanım [koşulları'ne gidin](https://aka.ms/catou).
3. Yeni **terimler'e tıklayın**.

   ![Azure AD'nin yeni kullanım koşulları ayarlarının ekran görüntüsü.](../media/azure-ad-guest-terms-of-use.png)

4. Ad ve **Görünen** **ad yazın**.
6. Kullanım **koşulları belgesi için**, oluşturduğunuz pdf dosyasına göz atarak dosyayı seçin.
7. Kullanım koşulları belgenizin dilini seçin.
8. Kullanıcıların **kullanım koşullarını 'a genişletmesini gerekli olarak ayarlayın.** 
9. Koşullu **Erişim'in** altında, Koşullu **Erişim ilkesi şablonla zorla listesinde** Koşullu erişim **ilkesi daha sonra oluştur'a tıklayın**.
10. **Oluştur'a tıklayın**.

Kullanım koşullarını oluşturduktan sonra, bir sonraki adım konuklara kullanım koşullarını görüntüleyen bir koşullu erişim ilkesi oluşturmaktır.

Koşullu erişim ilkesi oluşturmak için

1. Azure koşullu [erişim ilkeleri'ne gidin](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade).
2. Koşullu **Erişim | İlkeler** blade, Yeni **ilke'ye tıklayın**.
3. Ad **kutusuna** bir ad yazın.
4. **Atamalar'ın** altında Kullanıcılar **ve gruplar'a tıklayın**.
5. Kullanıcılar ve **gruplar blade'inde** Kullanıcıları **ve grupları seç'i**, ardından **Tüm konuklar ve dış kullanıcılar onay kutusunu** seçin.
6. **Atamalar'ın altında** Bulut **uygulamaları veya eylemleri'ne tıklayın**.
7. Ekle sekmesinde **Uygulamaları** **seç'i seçin ve** ardından Seç'e **tıklayın**.
8. Blade **seçin'de****, Microsoft Teams,** **Office 365 SharePoint Online'ı** ve grupları Outlook **ardından** Seç'e **tıklayın**.
9. Erişim **denetimleri'nin altında** **Ver'e tıklayın**.
10. Blade **ver'de** Konuk kullanım **koşulları'yı seçin ve** ardından Seç'e **tıklayın**.
11. Yeni **blade'de** , **İlkeyi etkinleştir'in altında** **Etkin'e tıklayın** ve sonra da Oluştur'a **tıklayın**.

Şimdi, bir konuk ilk kez kuruluş içeriğine, ekip veya siteye erişme girişiminde bulunarak kullanım koşullarını kabul etmek zorunda olacak.

> [!NOTE]
> Koşullu Erişim'i kullanmak için Azure AD Premium P1 gerekir. Daha fazla bilgi için bkz [. Koşullu Erişim nedir](/azure/active-directory/conditional-access/overview)?

### <a name="more-information"></a>Daha fazla bilgi

[Azure Active Directory kullanım koşulları](/azure/active-directory/conditional-access/terms-of-use)

## <a name="set-up-guest-access-reviews"></a>Konuk erişimi incelemelerini ayarlama

Azure AD'de erişim incelemeleri ile, çeşitli ekipler ve gruplara kullanıcı erişiminin düzenli olarak incelenmsini otomatik hale kullanabilirsiniz. Konukların özellikle erişim incelemesine gerek kalmaması için, konukların gerektiğinden daha uzun süre kuruluşun hassas bilgilerine erişimi korumalarına yardımcı olabilirsiniz.

Konuk erişimi incelemesini ayarlamak için

1. Kimlik Yönetimi [sayfasında, sol](https://portal.azure.com/#blade/Microsoft_AAD_ERM/DashboardBlade) menüde Access incelemeleri'ne **tıklayın**.
2. Yeni erişim **gözden geçir'e tıklayın**.
3. Grup + **Teams seçeneğini** belirtin.
4. Konuk kullanıcıların **olduğu Microsoft 365 kullanıcı grupları seçeneğini** belirleyin. Grupları **hariç tutmak istediğiniz grupları seç'e** tıklayın.
5. Yalnızca konuk **kullanıcılar seçeneğini belirtin ve** ardından Sonraki **: İncelemeler'e tıklayın**.
6. Gözden **geçirenleri seçin altında** Grup **Sahiplerini seçin**.
7. Geri **dönüş gözden geçirenleri seç'e** tıklayın, geri dönüş gözden geçirenlerin kimler olacağını seçin ve ardından Seç'e **tıklayın**.
8. Gözden **geçirmenin yinelenmesini belirtin altında** Üç **Aylık'ı seçin**.
9. Başlangıç tarihi ve süresini seçin.
10. End **için** Hiçbir **zaman'ı** seçin ve ardından Sonraki **: Tamam'Ayarlar**.

    ![Azure AD erişimini gözden geçirme sekmesinin ekran görüntüsü.](../media/azure-ad-create-access-review.png)

11. Uyumluluk **Ayarlar**, iş kurallarınıza uyumluluk ayarlarını gözden geçirebilirsiniz.

    ![Azure AD erişim gözden geçirme ayarları sekmesinin ekran görüntüsü.](../media/azure-ad-create-access-review-settings.png)

12. Sonraki **: Gözden Geçir + Oluştur'a tıklayın**.
13. Bir Gözden **Geçir adı yazın** ve ayarları gözden geçirin.
14. **Oluştur'a tıklayın**.

SharePoint ve OneDrive konumlarına bakılmaksızın, iç kullanıcılar belgeye erişmeye devam ederken, belgenin tüm konuklar için paylaşılıyor olup olmadığı bakılmaksızın, belgelerin hassas bilgileri algıladikten hemen sonra önceden engellenmiş olacağını unutmayın.

### <a name="more-information"></a>Daha fazla bilgi

[Azure AD erişim incelemeleriyle konuk erişimini yönetme](/azure/active-directory/governance/manage-guest-access-with-access-reviews)

[Azure AD erişim incelemesinde grupların veya uygulamaların erişim incelemesi oluşturma](/azure/active-directory/governance/create-access-review)

## <a name="set-up-web-only-access-for-guests"></a>Konuklar için yalnızca web erişimi ayarlama

Konukların yalnızca web tarayıcısını kullanarak ekiplerinize, sitenize ve dosyalarınıza erişmesini gerekli bulundurarak saldırı yüzeyinizi düşürerek yönetiminizi kolaylaştırabilirsiniz.

Daha Microsoft 365 grupları ve Teams için, bu işlem Azure AD koşullu erişim ilkesiyle yapılır. Daha SharePoint için, bu SharePoint merkezinde yapılandırılır. (Ayrıca, konukları [yalnızca web erişimiyle kısıtlamak için duyarlılık etiketlerini de kullanabilirsiniz](../compliance/sensitivity-labels-teams-groups-sites.md).)

Konukları Gruplar ve gruplar ve gruplar için yalnızca web erişimiyle kısıtlamak Teams:

1. Azure koşullu [erişim ilkeleri'ne gidin](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade).
2. Koşullu Erişim **- İlkeler blade'inde** Yeni **ilke'ye tıklayın**.
3. Ad **kutusuna** bir ad yazın.
4. **Atamalar'ın** altında Kullanıcılar **ve gruplar'a tıklayın**.
5. Kullanıcılar ve **gruplar blade'inde** Kullanıcıları **ve grupları seç'i**, ardından **Tüm konuklar ve dış kullanıcılar onay kutusunu** seçin.
6. **Atamalar'ın altında** Bulut **uygulamaları veya eylemleri'ne tıklayın**.
7. Ekle sekmesinde **Uygulamaları** **seç'i seçin ve** ardından Seç'e **tıklayın**.
8. Blade **seçin'de**, Tek **Microsoft Teams** **Grupları'Outlook ardından** Seç'e **tıklayın**.
9. **Ödevler'in altında** **Koşullar'a tıklayın**.
10. Koşullar **blade'inde** İstemci **uygulamaları'ne tıklayın**.
11. İstemci uygulamaları **blade'inde** Yapılandır için **Evet'e** tıklayın ve sonra Mobil uygulamalar ve masaüstü **istemcileri'Exchange ActiveSync** **istemcilerini** ve **Diğer Exchange ActiveSync ayarlarını** seçin. Tarayıcı **onay** kutusunu temizleyin.

    ![Azure AD koşullu erişim istemci uygulamaları ayarlarının ekran görüntüsü.](../media/azure-ad-conditional-access-client-mobile.png)

12. **Bitti'ye tıklayın**.
13. Erişim **denetimleri'nin altında** **Ver'e tıklayın**.
14. Grant **blade'de** Cihazın uyumlu **olarak işaretlenirken işaretlenir ve** Karma **Azure AD'ye bağlı cihaz gerektir'i seçin**.
15. Birden **çok denetim için** altında, **Seçilen denetimlerden birini gerektir'i seçin** ve ardından Seç'e **tıklayın**.
16. Yeni **blade'de** , **İlkeyi etkinleştir'in altında** **Etkin'e tıklayın** ve sonra da Oluştur'a **tıklayın**.

Konukların web'de web erişimine kısıtlamak SharePoint

1. Genel yönetim SharePoint İlkeler'i **genişletin ve Access** <a href="https://go.microsoft.com/fwlink/?linkid=2185071" target="_blank">**denetimi'ni seçin**</a>.
2. **Unmanaged devices öğesini seçin**.
3. Sınırlı, **yalnızca web erişimine izin ver seçeneğini ve** ardından Kaydet'i **seçin**.

Yönetim merkezinde bu ayarın, Azure AD SharePoint de desteklenen bir koşullu erişim ilkesi oluşturduğuna dikkat edin.

## <a name="configure-a-session-timeout-for-guests"></a>Konuklar için oturum zaman aşımı yapılandırma

Konukların düzenli olarak kimlik doğrulaması yapmalarını gerektirme, bir konuğun cihazı güvenli tutulmasa bile bilinmeyen kullanıcıların kuruluş içeriğine erişme olasılığını azaltabilirsiniz. Azure AD'de konuklar için oturum zaman aşımı koşullu erişim ilkesi yapılandırabilirsiniz.

Konuk oturumu zaman aşımı ilkesi yapılandırmak için

1. Azure koşullu [erişim ilkeleri'ne gidin](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade).
2. Koşullu Erişim **- İlkeler blade'inde** Yeni **ilke'ye tıklayın**.
3. Ad **kutusuna** Konuk oturumu zaman *aşımı yazın*.
4. **Atamalar'ın** altında Kullanıcılar **ve gruplar'a tıklayın**.
5. Kullanıcılar ve **gruplar blade'inde** Kullanıcıları **ve grupları seç'i**, ardından **Tüm konuklar ve dış kullanıcılar onay kutusunu** seçin.
6. **Atamalar'ın altında** Bulut **uygulamaları veya eylemleri'ne tıklayın**.
7. Ekle sekmesinde **Uygulamaları** **seç'i seçin ve** ardından Seç'e **tıklayın**.
8. Blade **seçin'de****, Microsoft Teams,** **Office 365 SharePoint Online'ı** ve grupları Outlook **ardından** Seç'e **tıklayın**.
9. Erişim **denetimleri altında Oturum'a** **tıklayın**.
10. Oturum **blade'inde** Oturum **açma sıklığı'ı seçin**.
11. Zaman **dönemi için 1** **ve** Gün'leri seçin ve ardından Seç'e **tıklayın**.
12. Yeni **blade'de** , **İlkeyi etkinleştir'in altında** **Etkin'e tıklayın** ve sonra da Oluştur'a **tıklayın**.

## <a name="create-a-sensitive-information-type-for-a-highly-sensitive-project"></a>Çok hassas bir proje için hassas bilgi türü oluşturma

Hassas bilgi türleri, ilke iş akışlarında uyumluluk gereksinimlerini zorunlu yapmak için  kullanılabilen önceden tanımlanmış dizedir. Uyumluluk Microsoft 365, sürücü numaraları, kredi kartı numaraları, banka hesap numaraları vb. dahil olmak üzere yüzden fazla hassas bilgi türüyle birlikte gelir.

Belirli içeriklerin yönetimine yardımcı olmak için, özel hassas bilgi türleri oluşturabilirsiniz. Bu örnekte, son derece hassas bir proje için özel bir hassas bilgi türü oluştur istiyoruz. Daha sonra otomatik olarak bir duyarlılık etiketi uygulamak için bu hassas bilgi türünü kullanabiliriz.

Hassas bir bilgi türü oluşturmak için

1. Uyumluluk [Microsoft 365 sol gezintide](https://compliance.microsoft.com) Sınıflandırma'yı **genişletin ve Hassas** bilgi **türleri'ne tıklayın**.
2. **Oluştur'a tıklayın**.
3. Ad **ve Açıklama** **için Satürn'Project** **Satürn** yazın ve Ardından Sonraki'ye **tıklayın**.
4. Öğe **ekle'ye tıklayın**.
5. İçeriği **algıla listesinde Anahtar** **sözcükler'i seçin** ve ardından anahtar sözcük *Project Satürn* yazın.
6. **Sonraki'ne** ve ardından Son'a **tıklayın**.
7. Hassas bilgi türünü test etmek istensin mi diye sorsanız, Hayır'a **tıklayın**.

### <a name="more-information"></a>Daha fazla bilgi

[Özel hassas bilgi türleri](/Office365/SecurityCompliance/custom-sensitive-info-types)

## <a name="create-an-auto-labeling-policy-to-assign-a-sensitivity-label-based-on-a-sensitive-information-type"></a>Hassas bir bilgi türüne dayalı bir duyarlılık etiketi atamak için otomatik etiket ilkesi oluşturma

Kuruluşta duyarlılık etiketleri kullanıyorsanız, tanımlı hassas bilgi türlerini içeren dosyalara otomatik olarak etiket uygulayabilirsiniz. 

Otomatik etiket ilkesi oluşturmak için

1. Uyumluluk [Microsoft 365 merkezini açın](https://compliance.microsoft.com).
2. Sol gezintide Bilgi **koruma'ya tıklayın**.
3. Otomatik **etiketleme sekmesinde Otomatik** etiket ilkesi **oluştur'a tıklayın**.
4. Bu **etiketin uygulanmasını istediğiniz bilgileri seçin sayfasında Özel'i** seçin ve **Sonra da Sonraki'yi** **tıklatın**.
5. İlke için bir ad ve açıklama yazın, ardından Sonraki'ye **tıklayın**.
6. Etiket **uygulamak istediğiniz konumları seçin sayfasında Siteleri seç'i** **SharePoint'yi** **tıklatın**.
7. Otomatik etiketlemeyi açmak istediğiniz sitelerin URL'lerini ekleyin ve Bitti'ye **tıklayın**.
8. **İleri**'ye tıklayın.
9. Ortak veya **gelişmiş kuralları ayarla sayfasında Ortak kurallar'ı** **seçin ve İleri'ye** **tıklayın**.
10. Tüm **konumlarda içerik için kural tanımla sayfasında Yeni** **kural'a tıklayın**.
11. Yeni kural **sayfasında kurala** bir ad verin, Koşul ekle'ye tıklayın **ve sonra İçerik** hassas bilgi **türleri içeriyor'a tıklayın**.
12. **Ekle'ye** tıklayın, **Hassas bilgi türleri'ne** tıklayın, kullanmak istediğiniz hassas bilgi türlerini seçin, Ekle'ye **tıklayın** ve sonra da Kaydet'e **tıklayın**.
13. **İleri**'ye tıklayın.
14. Etiket **seç'e** tıklayın, kullanmak istediğiniz etiketi seçin ve Ekle'ye **tıklayın**.
15. **İleri**'ye tıklayın.
16. Benzetim modunda ilkeyi bırakın ve Sonraki'ye **tıklayın**.
17. İlke **oluştur'a** ve sonra **Bitti'ye tıklayın**.

İlke uygulanırken, kullanıcı bir belgeye "Satürn Project adını yazınca, otomatik etiketleme ilkesi dosyayı tararken belirtilen etiketi otomatik olarak uygulayacaktır.

### <a name="more-information"></a>Daha fazla bilgi

[İçeriğe otomatik olarak bir hassasiyet etiketi uygulama](../compliance/apply-sensitivity-label-automatically.md)

## <a name="create-a-dlp-policy-to-remove-guest-access-to-highly-sensitive-files"></a>Çok hassas dosyalara konuk erişimini kaldırmak için DLP ilkesi oluşturma

Hassas içeriğin istenmeyen [konuk paylaşımını önlemek için veri kaybı önleme (DLP)](../compliance/dlp-learn-about-dlp.md) kullanabilirsiniz. Veri kaybını önleme, dosyanın duyarlılık etiketine bağlı olarak işlem kaldırabilir ve konuk erişimini kaldırabilir.

DLP kuralı oluşturmak için

1. Uyumluluk Microsoft 365 merkezinde Veri kaybı önleme [sayfasına gidin](https://compliance.microsoft.com/datalossprevention).
2. İlke **oluştur'a tıklayın**.
3. **Özel'i seçin** ve Sonraki'ne **tıklayın**.
4. İlke için bir ad yazın ve Sonraki'ye **tıklayın**.
5. **İlkenin uygulanıyor olduğu** konumlar sayfasında, site ve hesap ekleme  SharePoint tüm ayarları kapatın ve **OneDrive'e** **tıklayın**.
6. İlke **ayarlarını tanımla sayfasında** , Sonraki'ne **tıklayın**.
7. Gelişmiş **DLP kurallarını özelleştir sayfasında** Kural **oluştur'a tıklayın** ve kural için bir ad yazın.
8. **Koşullar'ın** altında Koşul **ekle'ye tıklayın** ve İçerik **içeriği'ne tıklayın**.
9. **Ekle'ye** tıklayın, **Duyarlılık etiketleri'ne** tıklayın, kullanmak istediğiniz etiketleri seçin ve Ekle'ye **tıklayın**.

   ![Durum seçeneklerinin, hassas bilgi türlerinin, duyarlılık etiketlerinin ve bekletme etiketlerinin ekran görüntüsü.](../media/limit-accidental-exposure-dlp-conditions.png)

10. **Eylemler'in** altında **Eylem ekle'ye** tıklayın **ve Bu konumlarda erişimi kısıtla veya içeriği Microsoft 365 seçin**.
11. Konumlarda **erişimi kısıtla veya içeriği Microsoft 365 onay** kutusunu seçin ve ardından Yalnızca kuruluş **dışındaki kişiler seçeneğini** belirtin.

      ![DLP kuralı eylem seçeneklerinin ekran görüntüsü.](../media/dlp-remove-guest-access-sensitive-files.png)

12. **Kaydet'e** ve sonra da Sonraki'ne **tıklayın**.
13. Test seçeneklerinizi seçin ve Sonraki'ye **tıklayın**.
14. **Gönder'e** ve ardından **Bitti'ye tıklayın**.

Konuk sitenin veya ekibin bir bütün olarak üyesi ise, bu ilkenin erişimi kaldırmaz. Bir sitede veya ekipte konuk üyelere sahip üst düzeyde hassas belgeler olmasını planlıyorsanız şu seçenekleri göz önünde bulundurabilirsiniz:

- Özel [kanallar kullanın](/MicrosoftTeams/private-channels) ve yalnızca özel kanallarda kuruluş üyelerinin izin vermesine izin verme.
- Paylaşılan [kanalları,](/MicrosoftTeams/shared-channels) yalnızca kuruluşun kendisinde yer alan ve organizasyon dışındaki çalışanlarla işbirliği yapmak için kullanın.

## <a name="additional-options"></a>Ek seçenekler

Web sitesi ve ağ bağlantılarında Microsoft 365 Azure Active Directory güvenliğinizi sağlamanıza yardımcı olacak bazı ek seçenekler vardır.

- Kullanıcıların kimlerle paylaşımda yer ala bir paylaşım etki alanı oluştura etki alanlarının izin verilen veya reddedilenler listesini oluşturabilirsiniz. Daha [fazla bilgi için bkz. SharePoint](/sharepoint/restricted-domains-sharing) ve OneDrive içeriği etki alanına göre paylaşmayı kısıtlama ve Belirli kuruluşlardan [B2B](/azure/active-directory/b2b/allow-deny-list) kullanıcılarına davetlere izin verme veya bu davetleri engelleme.
- Kullanıcılarının bağlanabilirsiniz diğer Azure Active Directory kiracılarını sınırlandırabilirsiniz. Bilgi [için Bkz. SaaS bulut uygulamalarına erişimi yönetmek için kiracı](/azure/active-directory/manage-apps/tenant-restrictions) kısıtlamalarını kullanma.
- İş ortaklarının konuk hesaplarını yönetmeye yardımcı olduğu yönetilen bir ortam oluşturabilirsiniz. Bilgi [için bkz. Yönetilen konuklarla B2B extranet](/Office365/Enterprise/b2b-extranet) oluşturma.

## <a name="see-also"></a>Ayrıca Bkz

[Konuklarla paylaşım sırasında dosyalarda yanlışlıkla açık kalma sürelerini sınırlama](share-limit-accidental-exposure.md)

[Kimliği doğrulanmamış kullanıcılarla dosya ve klasör paylaşmak için en iyi yöntemler](best-practices-anonymous-sharing.md)

[Yönetilen konuklarla B2B extranet oluşturma](b2b-extranet.md)
