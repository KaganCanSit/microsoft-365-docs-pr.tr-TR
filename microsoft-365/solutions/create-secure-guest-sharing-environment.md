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
description: Microsoft 365'te gelişmiş işbirliği için konuk erişimi sağlayan güvenli bir konuk paylaşım ortamı oluşturmaya yönelik kullanılabilir seçenekler hakkında bilgi edinin.
ms.openlocfilehash: 26daea8795084a87a2891a5dd04da172692990cb
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490929"
---
# <a name="create-a-secure-guest-sharing-environment"></a>Güvenli bir konuk paylaşım ortamı oluşturma

Bu makalede, Microsoft 365'te güvenli bir konuk paylaşım ortamı oluşturmaya yönelik çeşitli seçenekleri inceleyeceğiz. Bunlar, kullanılabilir seçenekler hakkında fikir vermek için örneklerdir. Kuruluşunuzun güvenlik ve uyumluluk gereksinimlerini karşılamak için bu yordamları farklı birleşimlerde kullanabilirsiniz.

Bu makale şunları içerir:

- Konuklar için çok faktörlü kimlik doğrulamasını ayarlama.
- Konuklar için bir kullanım koşulları ayarlama.
- Konukların ekipler ve siteler için izinlere ihtiyaç duymaya devam edip etmediğini düzenli aralıklarla doğrulamak için üç aylık konuk erişim gözden geçirmeleri ayarlama.
- Yönetilmeyen cihazlar için konukları yalnızca web erişimiyle kısıtlama.
- Konukların günlük kimlik doğrulamasını sağlamak için oturum zaman aşımı ilkesini yapılandırma.
- Son derece hassas bir proje için hassas bilgi türü oluşturma.
- Hassas bilgi türü içeren belgelere otomatik olarak duyarlılık etiketi atama.
- Duyarlılık etiketine sahip dosyalardan konuk erişimini otomatik olarak kaldırma.

Bu makalede açıklanan seçeneklerden bazıları, konukların Azure Active Directory'de bir hesabı olmasını gerektirir. Dosya ve klasörleri paylaştığınızda konukların dizine dahil edildiğinden emin olmak için[, Azure AD B2B Preview ile SharePoint ve OneDrive tümleştirmesini](/sharepoint/sharepoint-azureb2b-integration-preview) kullanın.

Bu makalede konuk paylaşım ayarlarını etkinleştirmeyi tartışmayacağımıza dikkat edin. Farklı senaryolar için konuk paylaşımını etkinleştirme hakkında ayrıntılı bilgi için bkz. [Kuruluşunuzun dışındaki kişilerle işbirliği](collaborate-with-people-outside-your-organization.md) yapmak.

## <a name="set-up-multi-factor-authentication-for-guests"></a>Konuklar için çok faktörlü kimlik doğrulamasını ayarlama

Çok faktörlü kimlik doğrulaması, bir hesabın tehlikeye girme olasılığını büyük ölçüde azaltır. Konuklar herhangi bir idare ilkesine veya en iyi deneyime uymayan kişisel e-posta hesaplarını kullandığından, konuklar için çok faktörlü kimlik doğrulaması gerektirmek özellikle önemlidir. Bir konuğun kullanıcı adı ve parolası çalınırsa, ikinci bir kimlik doğrulama faktörüne ihtiyaç duymanız bilinmeyen tarafların sitelerinize ve dosyalarınıza erişme olasılığını büyük ölçüde azaltır.

Bu örnekte, Azure Active Directory'de koşullu erişim ilkesi kullanarak konuklar için çok faktörlü kimlik doğrulamasını ayarlayacağız.

Konuklar için çok faktörlü kimlik doğrulamasını ayarlamak için

1. [Azure koşullu erişim ilkeleri'ne](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade) gidin.
2. **Koşullu Erişim | İlkeler** dikey penceresinde **Yeni ilke'ye** tıklayın.
3. **Ad** alanına bir ad yazın.
4. **Atamalar'ın** altında **Kullanıcılar ve gruplar'a** tıklayın.
5. **Kullanıcılar ve gruplar** dikey penceresinde **Kullanıcıları ve grupları seç'i** seçin, **Tüm konuklar ve dış kullanıcılar** onay kutusunu seçin.
6. **Atamalar'ın** altında **Bulut uygulamaları veya eylemleri'ne** tıklayın.
7. **Bulut uygulamaları veya eylemler** dikey penceresinde **Ekle** sekmesinde **Tüm bulut uygulamaları'nı** seçin.
8. **Erişim denetimleri'nin** altında **Ver'e** tıklayın.
9. **Ver** dikey penceresinde **Çok faktörlü kimlik doğrulaması gerektir** onay kutusunu seçin ve **seç'e** tıklayın.
10. **Yeni** dikey penceresindeki **İlkeyi etkinleştir'in** altında **Açık'a** ve ardından **Oluştur'a** tıklayın.

Artık, paylaşılan içeriğe, sitelere veya ekiplere erişebilmesi için konuğun çok faktörlü kimlik doğrulamasına kaydolması gerekecektir.

### <a name="more-information"></a>Daha fazla bilgi

[Azure AD çok faktörlü kimlik doğrulama dağıtımı planlama](/azure/active-directory/authentication/howto-mfa-getstarted)

## <a name="set-up-a-terms-of-use-for-guests"></a>Konuklar için kullanım koşulları ayarlama

Bazı durumlarda konuklar, kuruluşunuzla gizlilik sözleşmeleri veya diğer yasal sözleşmeler imzalamamış olabilir. Konuklardan, kendileriyle paylaşılan dosyalara erişmeden önce kullanım koşullarını kabul etmelerini zorunlu kılabilirsiniz. Kullanım koşulları, paylaşılan bir dosyaya veya siteye ilk kez erişmeye çalıştıkları zaman görüntülenebilir.

Kullanım koşulları oluşturmak için, önce belgeyi Word'de veya başka bir yazma programında oluşturmanız ve ardından .pdf dosyası olarak kaydetmeniz gerekir. Bu dosya daha sonra Azure AD yüklenebilir.

Azure AD kullanım koşulları oluşturmak için

1. Azure'da Genel Yönetici, Güvenlik Yöneticisi veya Koşullu Erişim Yöneticisi olarak oturum açın.
2. [Kullanım koşulları'na](https://aka.ms/catou) gidin.
3. **Yeni terimler'e** tıklayın.

   ![Azure AD yeni kullanım koşulları ayarlarının ekran görüntüsü.](../media/azure-ad-guest-terms-of-use.png)

4. **Ad** ve **Görünen ad** yazın.
6. **Kullanım koşulları belgesi** için, oluşturduğunuz pdf dosyasına gidin ve seçin.
7. Kullanım koşulları belgenizin dilini seçin.
8. **Kullanıcıların kullanım koşullarını genişletmesini gerektir** seçeneğini **Açık** olarak ayarlayın.
9. **Koşullu Erişim'in** altında, **Koşullu Erişim ilkesiyle zorla şablon** listesinde **Koşullu erişim ilkesi daha sonra oluştur'u** seçin.
10. **Oluştur'a** tıklayın.

Kullanım koşullarını oluşturduktan sonra, sonraki adım konuklara kullanım koşullarını görüntüleyen bir koşullu erişim ilkesi oluşturmaktır.

Koşullu erişim ilkesi oluşturmak için

1. [Azure koşullu erişim ilkeleri'ne](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade) gidin.
2. **Koşullu Erişim | İlkeler** dikey penceresinde **Yeni ilke'ye** tıklayın.
3. **Ad** kutusuna bir ad yazın.
4. **Atamalar'ın** altında **Kullanıcılar ve gruplar'a** tıklayın.
5. **Kullanıcılar ve gruplar** dikey penceresinde **Kullanıcıları ve grupları seç'i** seçin, **Tüm konuklar ve dış kullanıcılar** onay kutusunu seçin.
6. **Atamalar'ın** altında **Bulut uygulamaları veya eylemleri'ne** tıklayın.
7. **Ekle** sekmesinde **Uygulamaları seç'i** seçin ve **seç'e** tıklayın.
8. **Seç** dikey penceresinde **Microsoft Teams'i** seçin, **SharePoint Online ve** **Outlook Grupları'nı** Office 365 ve ardından **Seç'e** tıklayın.
9. **Erişim denetimleri'nin** altında **Ver'e** tıklayın.
10. **Ver** dikey penceresinde **Konuk kullanım koşulları'nı** seçin ve **seç'e** tıklayın.
11. **Yeni** dikey penceresindeki **İlkeyi etkinleştir'in** altında **Açık'a** ve ardından **Oluştur'a** tıklayın.

Şimdi, bir konuğun kuruluşunuzdaki içeriğe veya ekip veya siteye ilk kez erişmeye çalıştığında, kullanım koşullarını kabul etmeleri gerekecektir.

> [!NOTE]
> Koşullu Erişim kullanmak için Azure AD Premium P1 lisansı gerekir. Daha fazla bilgi için bkz. [Koşullu Erişim nedir](/azure/active-directory/conditional-access/overview)?

### <a name="more-information"></a>Daha fazla bilgi

[Azure Active Directory kullanım koşulları](/azure/active-directory/conditional-access/terms-of-use)

## <a name="set-up-guest-access-reviews"></a>Konuk erişimi gözden geçirmelerini ayarlama

Azure AD'daki erişim gözden geçirmeleriyle, çeşitli ekiplere ve gruplara kullanıcı erişiminin düzenli olarak gözden geçirilmesini otomatikleştirebilirsiniz. Konuklar için özel olarak bir erişim gözden geçirmesi gerektirerek, konukların kuruluşunuzun hassas bilgilerine erişimi gerekenden daha uzun süre saklamamalarına yardımcı olabilirsiniz.

Konuk erişimi gözden geçirmesini ayarlamak için

1. [Kimlik İdaresi sayfasında](https://portal.azure.com/#blade/Microsoft_AAD_ERM/DashboardBlade), soldaki menüde **Access gözden geçirmeleri'ne** tıklayın.
2. **Yeni erişim gözden geçirme'ye** tıklayın.
3. **Teams + Gruplar** seçeneğini belirleyin.
4. **Konuk kullanıcıları olan Tüm Microsoft 365 grupları** seçeneğini belirleyin. Herhangi bir **grubu dışlamak istiyorsanız dışlamak** için Grupları seç'e tıklayın.
5. **Yalnızca konuk kullanıcılar** seçeneğini belirleyin ve ardından **İleri: Gözden Geçirmeler'e** tıklayın.
6. **Gözden geçirenleri seçin'in** altında **Grup Sahipleri'ni** seçin.
7. **Geri dönüş gözden geçirenleri seç'e** tıklayın, geri dönüş gözden geçirenlerin kim olacağını seçin ve ardından **Seç'e** tıklayın.
8. **Gözden geçirmenin yinelenme değerini belirtin altında** **Üç aylık seçeneğini** belirleyin.
9. Başlangıç tarihini ve süresini seçin.
10. **Bitiş** için **Hiçbir Zaman'ı** seçin ve ardından **İleri: Ayarlar'a** tıklayın.

    ![Azure AD erişim gözden geçirme sekmesinin ekran görüntüsü.](../media/azure-ad-create-access-review.png)

11. **Ayarlar** sekmesinde, iş kurallarınızla uyumluluk ayarlarını gözden geçirin.

    ![Azure AD erişim gözden geçirme ayarları sekmesinin ekran görüntüsü.](../media/azure-ad-create-access-review-settings.png)

12. **İleri: Gözden Geçir + Oluştur'a** tıklayın.
13. **Gözden geçir adı** yazın ve ayarları gözden geçirin.
14. **Oluştur'a** tıklayın.

SharePoint ve OneDrive konumlarında, belgenin tüm konuklar için paylaşılıp paylaşılmadığına bakılmaksızın, hassas bilgiler algılandığında belgelerin proaktif olarak engellendiğini, ancak iç kullanıcıların belgeye erişmeye devam edeceklerini unutmayın.

### <a name="more-information"></a>Daha fazla bilgi

[Azure AD erişim gözden geçirmeleriyle konuk erişimini yönetme](/azure/active-directory/governance/manage-guest-access-with-access-reviews)

[Azure AD erişim gözden geçirmelerinde grupların veya uygulamaların erişim gözden geçirmesini oluşturma](/azure/active-directory/governance/create-access-review)

## <a name="set-up-web-only-access-for-guests"></a>Konuklar için yalnızca web erişimi ayarlama

Konukların yalnızca bir web tarayıcısı kullanarak ekiplerinize, sitelerinize ve dosyalarınıza erişmesini zorunlu kılabilirsiniz. Bu, hassas dosyaları indirme ve yönetilmeyen bir cihazda bırakma olasılığını azaltır. Bu, paylaşılan cihazları kullanan ortamlarla paylaşım yaparken de kullanışlıdır.

Microsoft 365 Grupları ve Teams için bu, Azure AD bir koşullu erişim ilkesiyle yapılır. SharePoint için bu, SharePoint yönetim merkezinde yapılandırılır. (Konukları [yalnızca web erişimine kısıtlamak için duyarlılık etiketlerini de kullanabilirsiniz](../compliance/sensitivity-labels-teams-groups-sites.md).)

Grupların ve Teams'in konukları yalnızca web erişimine kısıtlamak için:

1. [Azure koşullu erişim ilkeleri'ne](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade) gidin.
2. **Koşullu Erişim - İlkeler** dikey penceresinde **Yeni ilke'ye** tıklayın.
3. **Ad** kutusuna bir ad yazın.
4. **Atamalar'ın** altında **Kullanıcılar ve gruplar'a** tıklayın.
5. **Kullanıcılar ve gruplar** dikey penceresinde **Kullanıcıları ve grupları seç'i** seçin, **Tüm konuklar ve dış kullanıcılar** onay kutusunu seçin.
6. **Atamalar'ın** altında **Bulut uygulamaları veya eylemleri'ne** tıklayın.
7. **Ekle** sekmesinde **Uygulamaları seç'i** seçin ve **seç'e** tıklayın.
8. **Seç** dikey penceresinde **Microsoft Teams** ve **Outlook Grupları'nı** seçin ve **seç'e** tıklayın.
9. **Atamalar'ın** altında **Koşullar'a** tıklayın.
10. **Koşullar** dikey penceresinde **İstemci uygulamaları'na** tıklayın.
11. **İstemci uygulamaları** dikey penceresinde **Yapılandır için Evet'e** tıklayın ve ardından **Mobil uygulamalar ve masaüstü istemcileri**, **Exchange ActiveSync istemciler** ve **Diğer istemciler** ayarlarını seçin. **Tarayıcı** onay kutusunu temizleyin.

    ![Azure AD koşullu erişim istemci uygulamaları ayarlarının ekran görüntüsü.](../media/azure-ad-conditional-access-client-mobile.png)

12. **Bitti'ye** tıklayın.
13. **Erişim denetimleri'nin** altında **Ver'e** tıklayın.
14. **Ver** dikey penceresinde **Cihazın uyumlu olarak işaretlenmesini gerektir** ve **Karma Azure AD katılmış cihaz gerektir'i** seçin.
15. **Birden çok denetim için'in** altında **Seçili denetimlerden birini gerektir'i** seçin ve seç'e **tıklayın**.
16. **Yeni** dikey penceresindeki **İlkeyi etkinleştir'in** altında **Açık'a** ve ardından **Oluştur'a** tıklayın.

SharePoint'te konukları web tabanlı erişimle sınırlamak için

1. SharePoint yönetim merkezinde **İlkeler'i** genişletin ve <a href="https://go.microsoft.com/fwlink/?linkid=2185071" target="_blank">**Erişim denetimi'ni**</a> seçin.
2. **Yönetilmeyen cihazlar'ı** seçin.
3. **Sınırlı, yalnızca web erişimine izin ver** seçeneğini ve ardından **Kaydet'i** seçin.

SharePoint yönetim merkezindeki bu ayarın Azure AD'da destekleyici bir koşullu erişim ilkesi oluşturduğunu unutmayın.

## <a name="configure-a-session-timeout-for-guests"></a>Konuklar için oturum zaman aşımı yapılandırma

Konukların düzenli olarak kimlik doğrulaması yapmalarını zorunlu tutmak, bir konuğun cihazı güvenli tutulmazsa bilinmeyen kullanıcıların kuruluşunuzun içeriğine erişme olasılığını azaltabilir. Azure AD'da konuklar için oturum zaman aşımı koşullu erişim ilkesi yapılandırabilirsiniz.

Konuk oturumu zaman aşımı ilkesini yapılandırmak için

1. [Azure koşullu erişim ilkeleri'ne](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade) gidin.
2. **Koşullu Erişim - İlkeler** dikey penceresinde **Yeni ilke'ye** tıklayın.
3. **Ad** kutusuna *Konuk oturumu zaman aşımı* yazın.
4. **Atamalar'ın** altında **Kullanıcılar ve gruplar'a** tıklayın.
5. **Kullanıcılar ve gruplar** dikey penceresinde **Kullanıcıları ve grupları seç'i** seçin, **Tüm konuklar ve dış kullanıcılar** onay kutusunu seçin.
6. **Atamalar'ın** altında **Bulut uygulamaları veya eylemleri'ne** tıklayın.
7. **Ekle** sekmesinde **Uygulamaları seç'i** seçin ve **seç'e** tıklayın.
8. **Seç** dikey penceresinde **Microsoft Teams'i** seçin, **SharePoint Online ve** **Outlook Grupları'nı** Office 365 ve ardından **Seç'e** tıklayın.
9. **Erişim denetimleri'nin** altında **Oturum'a** tıklayın.
10. **Oturum** dikey penceresinde **Oturum açma sıklığı'nı** seçin.
11. Dönem için **1** ve **Günler'i** seçin ve **seç'e** tıklayın.
12. **Yeni** dikey penceresindeki **İlkeyi etkinleştir'in** altında **Açık'a** ve ardından **Oluştur'a** tıklayın.

## <a name="create-a-sensitive-information-type-for-a-highly-sensitive-project"></a>Son derece hassas bir proje için hassas bilgi türü oluşturma

Hassas bilgi türleri, uyumluluk gereksinimlerini zorlamak için ilke iş akışlarında kullanılabilecek önceden tanımlanmış dizelerdir. Microsoft Purview uyumluluk portalı, sürücü belgesi numaraları, kredi kartı numaraları, banka hesap numaraları vb. dahil olmak üzere yüzden fazla hassas bilgi türüyle birlikte gelir.

Kuruluşunuza özgü içerikleri yönetmeye yardımcı olmak için özel hassas bilgi türleri oluşturabilirsiniz. Bu örnekte, son derece hassas bir proje için özel bir hassas bilgi türü oluşturacağız. Bu hassas bilgi türünü daha sonra otomatik olarak duyarlılık etiketi uygulamak için kullanabiliriz.

Hassas bilgi türü oluşturmak için

1. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com) sol gezinti bölmesinde **Sınıflandırma'yı** genişletin ve **hassas bilgi türleri'ne** tıklayın.
2. **Oluştur'a** tıklayın.
3. **Ad** ve **Açıklama** için **Project Saturn** yazın ve **İleri'ye** tıklayın.
4. **Öğe ekle'ye** tıklayın.
5. **İçerik içeren içeriği algıla** listesinde **Anahtar Sözcükler'i** seçin ve anahtar sözcük kutusuna *Project Saturn* yazın.
6. **İleri'ye** ve ardından **Son'a** tıklayın.
7. Hassas bilgi türünü test etmek isteyip istemediyseniz **Hayır'a** tıklayın.

### <a name="more-information"></a>Daha fazla bilgi

[Özel hassas bilgi türleri](/Office365/SecurityCompliance/custom-sensitive-info-types)

## <a name="create-an-auto-labeling-policy-to-assign-a-sensitivity-label-based-on-a-sensitive-information-type"></a>Hassas bilgi türüne göre duyarlılık etiketi atamak için otomatik etiketleme ilkesi oluşturma

Kuruluşunuzda duyarlılık etiketleri kullanıyorsanız, tanımlı hassas bilgi türleri içeren dosyalara otomatik olarak bir etiket uygulayabilirsiniz. 

Otomatik etiketleme ilkesi oluşturmak için

1. [Microsoft Purview yönetim merkezini](https://compliance.microsoft.com) açın.
2. Sol gezinti bölmesinde **Bilgi koruması'na** tıklayın.
3. **Otomatik etiketleme** sekmesinde **Otomatik etiketleme ilkesi oluştur'a** tıklayın.
4. **Bu etiketin uygulanmasını istediğiniz bilgileri seçin sayfasında Özel'i** seçin ve **İleri'ye** tıklayın.
5. İlke için bir ad ve açıklama yazın ve **İleri'ye** tıklayın.
6. **Etiket uygulamak istediğiniz konumları seçin** sayfasında **SharePoint sitelerini** açın ve **Siteleri seç'e** tıklayın.
7. Otomatik etiketlemeyi açmak istediğiniz sitelerin URL'lerini ekleyin ve **Bitti'ye** tıklayın.
8. **İleri**'ye tıklayın.
9. **Ortak veya gelişmiş kuralları ayarla** sayfasında **Ortak kurallar'ı** seçin ve **İleri'ye** tıklayın.
10. **Tüm konumlarda içerik için kural tanımla** sayfasında **Yeni kural'a** tıklayın.
11. **Yeni kural** sayfasında kurala bir ad verin, **Koşul ekle'ye** tıklayın ve ardından **İçerik hassas bilgi türleri içeriyor'a** tıklayın.
12. **Ekle'ye** tıklayın, **Hassas bilgi türleri'ne** tıklayın, kullanmak istediğiniz hassas bilgi türlerini seçin, **Ekle'ye** tıklayın ve ardından **Kaydet'e** tıklayın.
13. **İleri**'ye tıklayın.
14. **Etiket seçin'e** tıklayın, kullanmak istediğiniz etiketi seçin ve **ekle'ye** tıklayın.
15. **İleri**'ye tıklayın.
16. İlkeyi simülasyon modunda bırakın ve **İleri'ye** tıklayın.
17. **İlke oluştur'a** ve ardından **Bitti'ye** tıklayın.

İlke uygulandığında, kullanıcı belgeye "Project Saturn" yazdığınızda, otomatik etiketleme ilkesi dosyayı taradığında belirtilen etiketi otomatik olarak uygular.

### <a name="more-information"></a>Daha fazla bilgi

[İçeriğe otomatik olarak bir hassasiyet etiketi uygulama](../compliance/apply-sensitivity-label-automatically.md)

## <a name="create-a-dlp-policy-to-remove-guest-access-to-highly-sensitive-files"></a>Son derece hassas dosyalara konuk erişimini kaldırmak için DLP ilkesi oluşturma

hassas içeriğin istenmeyen konuk paylaşımını önlemek için [Microsoft Purview Veri Kaybı Önleme (DLP)](../compliance/dlp-learn-about-dlp.md) kullanabilirsiniz. Veri kaybı önleme, bir dosyanın duyarlılık etiketine göre işlem yapabilir ve konuk erişimini kaldırabilir.

DLP kuralı oluşturmak için

1. Microsoft Purview yönetim merkezinde [Veri kaybı önleme sayfasına](https://compliance.microsoft.com/datalossprevention) gidin.
2. **İlke oluştur'a** tıklayın.
3. **Özel'i** seçin ve **İleri'ye** tıklayın.
4. İlke için bir ad yazın ve **İleri'ye** tıklayın.
5. **İlkenin uygulanacağı konumlar** sayfasında **, SharePoint siteleri** ve **OneDrive hesapları** dışındaki tüm ayarları kapatın ve **ardından İleri'ye** tıklayın.
6. **İlke ayarlarını tanımla** sayfasında **İleri'ye** tıklayın.
7. **Gelişmiş DLP kurallarını özelleştir** sayfasında **Kural oluştur'a** tıklayın ve kural için bir ad yazın.
8. **Koşullar'ın** altında **Koşul ekle'ye** tıklayın ve **İçerik içerir'i** seçin.
9. **Ekle'ye** tıklayın, **Duyarlılık etiketleri'ni** seçin, kullanmak istediğiniz etiketleri seçin ve **Ekle'ye** tıklayın.

   ![Koşul seçeneklerinin, hassas bilgi türlerinin, duyarlılık etiketlerinin ve bekletme etiketlerinin ekran görüntüsü.](../media/limit-accidental-exposure-dlp-conditions.png)

10. **Eylemler'in** altında **Eylem ekle'ye** tıklayın ve **Erişimi kısıtla veya Microsoft 365 konumlarındaki içeriği şifrele'yi** seçin.
11. **Erişimi kısıtla veya Microsoft 365 konumlarındaki içeriği şifrele** onay kutusunu seçin ve ardından **Yalnızca kuruluşunuzun dışındaki kişiler** seçeneğini belirleyin.

      ![DLP kuralı eylem seçeneklerinin ekran görüntüsü.](../media/dlp-remove-guest-access-sensitive-files.png)

12. **Kaydet'e** ve ardından **İleri'ye** tıklayın.
13. Test seçeneklerinizi belirleyin ve **İleri'ye** tıklayın.
14. **Gönder'e** ve ardından **Bitti'ye** tıklayın.

Konuk sitenin veya ekibin bir bütün olarak üyesiyse bu ilkenin erişimi kaldırmadığını unutmayın. Konuk üyeleri olan bir sitede veya ekipte son derece hassas belgeler olmasını planlıyorsanız şu seçenekleri göz önünde bulundurun:

- [Özel kanalları](/MicrosoftTeams/private-channels) kullanın ve yalnızca özel kanallarda kuruluşunuzun üyelerine izin verin.
- Paylaşılan [kanalları](/MicrosoftTeams/shared-channels) kullanarak kuruluşunuzun dışındaki kişilerle işbirliği yaparken, yalnızca kuruluşunuzdaki kişilerin ekibin içinde olmasını sağlayın.

## <a name="additional-options"></a>Ek seçenekler

Microsoft 365 ve Azure Active Directory'de konuk paylaşım ortamınızın güvenliğini sağlamaya yardımcı olabilecek bazı ek seçenekler vardır.

- Kullanıcıların paylaşabileceği kişileri sınırlamak için izin verilen veya reddedilen paylaşım etki alanlarının listesini oluşturabilirsiniz. Daha fazla bilgi için bkz [. SharePoint ve OneDrive içeriğinin etki alanına göre paylaşımını kısıtlama](/sharepoint/restricted-domains-sharing) ve [B2B kullanıcılarına belirli kuruluşlardan gelen davetlere izin verme veya engelleme](/azure/active-directory/b2b/allow-deny-list) .
- Kullanıcılarınızın bağlanabileceği diğer Azure Active Directory kiracılarını sınırlayabilirsiniz. Bilgi için bkz. [SaaS bulut uygulamalarına erişimi yönetmek için kiracı kısıtlamalarını kullanma](/azure/active-directory/manage-apps/tenant-restrictions) .
- İş ortaklarının konuk hesaplarını yönetmeye yardımcı olabileceği bir yönetilen ortam oluşturabilirsiniz. Bilgi için bkz. [Yönetilen konuklarla B2B extranet oluşturma](/Office365/Enterprise/b2b-extranet) .

## <a name="see-also"></a>Ayrıca Bkz

[Konuklarla paylaşırken dosyaların yanlışlıkla açığa alınmasını sınırlayın](share-limit-accidental-exposure.md)

[Kimliği doğrulanmamış kullanıcılarla dosya ve klasör paylaşmaya yönelik en iyi yöntemler](best-practices-anonymous-sharing.md)

[Yönetilen konuklarla B2B extranet oluşturma](b2b-extranet.md)
