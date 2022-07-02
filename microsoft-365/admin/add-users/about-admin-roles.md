---
title: Microsoft 365 yönetim merkezinde, yönetici rolleri
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
- adminvideo
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: da585eea-f576-4f55-a1e0-87090b6aaa9d
description: Belirli işletme işlevlerine eşlenen ve yönetim merkezinde belirli görevleri yerine getirmek için izinler veren Hizmet yöneticisi gibi yönetici rolleri hakkında daha fazla bilgi edinin.
ms.openlocfilehash: cd40eb3421abf21205aac909fa2cb1796d7f0aa2
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2022
ms.locfileid: "66601982"
---
# <a name="about-admin-roles-in-the-microsoft-365-admin-center"></a>Microsoft 365 yönetim merkezinde, yönetici rolleri

YouTube'da [Microsoft 365 küçük işletme yardımına](https://go.microsoft.com/fwlink/?linkid=2197659) göz atın.

Microsoft 365 veya Office 365 aboneliği, <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezini</a> kullanarak kuruluşunuzdaki kullanıcılara atayabileceğiniz bir dizi yönetici rolü ile birlikte gelir. Her bir yönetici rolü, işletme ile ilgili genel işlevlere yöneliktir ve kuruluşunuzdaki kişilere, yönetim merkezlerinde belirli görevler yapma izni verir.

<a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a>, Azure AD rollerini ve Microsoft Intune rollerini yönetmenizi sağlar. Fakat bu roller, Azure AD portalında ve Intune yönetim merkezinde kullanılabilen rollerin alt kümesidir.

> [!TIP]
> Bu konuda verilen adımlarla ilgili yardıma ihtiyacınız varsa[bir Microsoft küçük işletme uzmanıyla çalışmayı](https://go.microsoft.com/fwlink/?linkid=2186871) göz önünde bulundurun. İşletme Yardımı ile, işletmenizi büyütürken işe alımdan gündelik kullanıma kadar her aşamada siz ve çalışanlarınız günün 24 saati küçük işletme uzmanlarına erişebilirsiniz.

## <a name="watch-what-is-an-admin"></a>İzleyin: Yönetici nedir?

[YouTube kanalımızda](https://go.microsoft.com/fwlink/?linkid=2198028) bu videoya ve diğer videolara göz atın.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1SRc0]

1. Microsoft 365’te oturum açtığınızda uygulama başlatıcıyı seçin. Yönetici düğmesini görüyorsanız yöneticisiniz demektir.
1. Microsoft 365 yönetim merkezine gitmek için **Yönetici**'yi seçin.
1. Sol gezinti bölmesinde, **Kullanıcılar** > > <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**Etkin Kullanıcılar**</a> seçeneğini belirtin.
1. Yönetici yapmak istediğiniz kişiyi seçin. Kullanıcının ayrıntıları sağdaki iletişim kutusunda görüntülenir.

## <a name="before-you-begin"></a>Başlamadan önce

<a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezinde</a> yönetebileceğiniz ayrıntılı Azure AD rolü açıklamalarının tam listesini mi arıyorsunuz? [Azure Active Directory'de yönetici rolü izinleri[’ne göz atın. [Azure AD yerleşik rolleri](/azure/active-directory/roles/permissions-reference).

<a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezinde</a> yönetebileceğiniz ayrıntılı Intune rol açıklamalarının tam listesini mi arıyorsunuz?  [Microsoft Intune ile Rol tabanlı erişim denetimine (RBAC)](/mem/intune/fundamentals/role-based-access-control) göz atın.

<a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezinde</a> rol atama hakkında daha fazla bilgi için bkz. [Yönetici rolleri atama](assign-admin-roles.md).

## <a name="security-guidelines-for-assigning-roles"></a>Rol atamaya yönelik güvenlik yönergeleri

Yöneticilerin hassas verilere ve dosyalara erişimi olduğundan, kuruluşunuzun verilerinin daha güvenli kalması için bu yönergeleri izlemenizi öneririz.

| Öneri                  | Bu neden önemlidir?                 |
| :------------------- | :------------------- |
| 2 ila 4 arasında genel yönetici belirleyin  | Bir genel yönetici parolasını yalnızca başka bir genel yönetici sıfırlayabileceği için, hesap kilitlenmesi durumunda kuruluşunuzda en az 2 genel yönetici bulundurmanızı öneririz. Ancak genel yönetici, kuruluşunuzun ayarlarına ve verilerin çoğuna neredeyse sınırsız erişime sahiptir, bu nedenle 4 ' ten fazla genel yönetici bulundurmamanızı öneririz, çünkü bu bir güvenlik tehdidi olur. |
| *En az izin verilen* rolü atama    | *En az izin verilen* rolün atanması, yöneticilere yalnızca işin yapılmasını sağlamak için gereken erişimi verme anlamına gelir. Örneğin, bir kişinin çalışan parolalarını sıfırlamasını istiyorsanız, sınırsız genel yönetici rolünü atamamalısınız, parola Yöneticisi veya Yardım Masası Yöneticisi gibi sınırlı bir yönetim rolü atamalısınız. Bu, verilerinizin güvenliğini korumaya yardımcı olur.                 |
| Yöneticiler için çok faktörlü kimlik doğrulaması gerektirme                  |    Kullanıcılarınızın tüm kullanıcılarınız için ÇFKD gerektirmek iyi bir fikirdir olsa da, yöneticilerin kesinlikle giriş yapmak için ÇFKD kullanması gerekmelidir. ÇFKD, kullanıcıların söyledikleri kişi olduklarını doğrulamak için ikinci bir tanımlama yöntemi girmesini sağlar. Yöneticiler, müşteri ve çalışan verilerinin çoğuna erişebilir ve ÇFKD gerektirirseniz, yöneticinin şifresi ele geçirilse bile, şifre ikinci kimlik formu olmadan işe yaramaz.  <br><br>ÇFKD'yi açtığınızda, kullanıcının bir dahaki sefer oturum açtığında hesap kurtarma için alternatif bir e-posta adresi ve telefon numarası sağlaması gerekecektir.  <br> [Çok faktörlü kimlik doğrulamasını ayarlama](../security-and-compliance/set-up-multi-factor-authentication.md)          |

Yönetim merkezinde bir ayarı veya sayfayı düzenleme izniniz olmadığını söyleyen bir ileti alırsanız, bunun nedeni bu izne sahip olmayan bir role atanmış olmanızdır.

## <a name="commonly-used-microsoft-365-admin-center-roles"></a>Yaygın olarak kullanılan Microsoft 365 yönetim merkezi rolleri

Microsoft 365 yönetim merkezinde, <a href="https://go.microsoft.com/fwlink/p/?linkid=2097861" target="_blank">**Rol atamaları**</a> öğesine gidip herhangi bir rolü seçebilirsiniz. Bu role atanan yöneticilerin neler yapmaya izninin olduğu ayrıntılı listeyi görüntülemek için **İzinler** sekmesini seçin. **Atanan** veya **Atanan yöneticiler** sekmesini seçerek kullanıcıları rollere ekleyin.

Muhtemelen kuruluşunuzda yalnızca aşağıdaki rolleri atamanız gerekecek. Varsayılan olarak öncelikle, çoğu kuruluşun kullandığı rolleri gösteririz. Rolü bulamıyorsanız, listenin en altına gidin ve **Tümünü Kategoriye Göre Göster** seçeneğini belirtin. (Rolle ilişkilendirilmiş cmdlet'ler de dahil olmak üzere ayrıntılı bilgi için bkz.[Azure AD yerleşik rolleri](/azure/active-directory/roles/permissions-reference).)

|Yönetici rolü     |Bu role kim atanmalıdır?  |
|---------|---------|
|Faturalama yöneticisi     |   Satın alma işlemi yapan, abonelikleri ve hizmet isteklerini yöneten ve hizmet durumunu izleyen kullanıcılara Faturalama yöneticisi rolünü atayın. <br><br> Faturalama yöneticileri şunları da yapabilir:<br> - Faturalamanın tüm özelliklerini yönetme <br> - Azure portalında destek bileti oluşturma ve yönetme <br>  |
|Exchange yöneticisi     |   Kullanıcılarınızın e-posta kutularını, Microsoft 365 gruplarını ve Exchange Online'ı görüntüleyip yönetmesi gereken kullanıcılara Exchange yöneticisi rolünü atayın. <br><br> Exchange yöneticileri aynı zamanda şunları da yapabilir:<br> - Bir kullanıcının posta kutusundaki silinen öğeleri kurtarma <br> -"Olarak Gönder" ve "Adına gönder" temsilcilerini ayarlama <br>  |
|Genel yönetici     |   Genel yönetici rolünü, Microsoft çevrimiçi hizmetlerindeki çoğu yönetim özellikleri ve verilere ulaşması gereken kullanıcılara atayın. <br><br> Gereğinden fazla sayıda kullanıcıya genel erişim vermek bir güvenlik riskidir ve 2 ila 4 arasında Genel yönetici belirlemenizi tavsiye ediyoruz. <br><br> Sadece genel yöneticiler şunları yapabilir:<br> - Tüm kullanıcılar için parola sıfırlama <br> - Etki alanları ekleme ve yönetme <br> - Başka bir genel yöneticinin engellemesini kaldırma <br> <br> **Not:**   Microsoft çevrimiçi hizmetler’e kaydolan kullanıcı otomatik olarak genel yönetici olur. |
|Genel gözetmen    |   Genel bir yöneticinin görüntüleyebileceği yönetim merkezlerinde yönetici özelliklerini ve ayarlarını görüntülemeye gerek duyan kullanıcılara genel gözetmen rolünü atayın. Genel gözetmen yönetici, hiçbir ayarı düzenleyemez.   |
|Gruplar yöneticisi     |   Microsoft 365 yönetim merkezi ve Azure Active Directory portalı da dahil olmak üzere, tüm grup ayarlarını yönetici merkezlerinde yönetmesi gereken kullanıcılara gruplar yöneticisi rolünü atayın. <br><br> Grup yöneticileri şunları yapabilir:<br> - Microsoft 365 grupları oluşturma, düzenleme, silme ve geri yükleme <br> -Grup oluşturma, süre sonu ve adlandırma ilkeleri oluşturma ve güncelleştirme <br> -Azure Active Directory güvenlik gruplarını oluşturma, düzenleme, silme ve geri yükleme| 
|Yardım Masası Yöneticisi     |   Aşağıdaki işlemi yapmasına gerek duyan kullanıcılara yardım masası yönetici rolünü atayın:<br> - Parolaları sıfırlama <br> - Kullanıcıları oturumu kapatmaya zorlama <br> - Hizmet isteklerini yönetme  <br> - Hizmet durumunu görüntüleme <br> <br> **Not**: Yardım Masası Yöneticisi yalnızca yönetici olmayan kullanıcılara ve kullanıcılara şu rollere sahip olmak için yardım edebilir: Dizin gözetmeni, Konuk davetli, Yardım masası Yöneticisi, İleti merkezi gözetmeni ve Rapor gözetmeni.      |
|Lisans yöneticisi    |   Kullanıcılara lisans ataması, kullanıcıların lisanslarını kaldırması ve kullanım konumlarını düzenlemesi gereken kullanıcılara Lisans yöneticisi rolünü atayın. <br/><br/> Lisans yöneticileri şunları da yapabilir: <br> - Grup tabanlı lisanslama için lisans atamalarını yeniden işleme <br> - Grup tabanlı lisanslama için gruplara ürün lisansları atama  |
|Office Uygulamaları yöneticisi    |   Aşağıdaki işlemi yapmasına gerek duyan kullanıcılara Office Uygulamaları yöneticisi rolünü atayın: <br> -Office bulut ilkesi hizmetini kullanarak Office için bulut tabanlı ilkeler oluşturma ve yönetme <br> - Hizmet istekleri oluşturma ve yönetme <br> - Kullanıcıların kendi Office uygulamalarında gördüğü Yenilikler içeriğini yönetme   <br> - Hizmet durumunu görüntüleme  |
|Parola yöneticisi  |   - Yönetici olmayanların ve Parola Yöneticilerinin parolalarını sıfırlaması gereken bir kullanıcıya Parola yöneticisi rolünü atayın.   |
|Message merkezi gözetmeni |   Aşağıdaki işlemleri yapması gereken kullanıcılara İleti merkezi okuyucusu rolünü atayın: <br> - İleti merkezi bildirimlerini izleme <br> - İleti merkezi gönderileri ve güncelleştirmelerinin haftalık e-posta özetlerini alma <br> - İleti merkezi gönderilerini paylaşma <br> - Kullanıcılar ve gruplar gibi Azure AD hizmetleri için salt okunur erişime sahip olma|
|Power Platform yöneticisi |   Aşağıdaki işlemleri yapması gereken kullanıcılara Power Platform yöneticisi rolünü atayın: <br> - Power Apps, Power Automate ve Microsoft Purview Veri Kaybını Önleme için tüm yönetici özelliklerini yönetme <br> - Hizmet istekleri oluşturma ve yönetme <br> - Hizmet durumunu görüntüleme  |
|Rapor gözetmeni |   Aşağıdaki işlemleri yapması gereken kullanıcılara Rapor okuyucusu rolünü atayın: <br> - Microsoft 365 yönetim merkezindeki kullanım verilerini ve etkinlik raporlarını görüntüleme <br> - Power BI benimseme içerik paketine erişme <br> - Azure AD'de oturum açma raporlarına ve etkinliğine erişme <br> - Microsoft Graph raporlama API'si tarafından döndürülen verileri görüntüleme|
|Hizmet Desteği yöneticisi   |   Normal yönetici rollerine ek olarak aşağıdakileri yapması gereken yöneticilere veya kullanıcılara ek bir rol olarak Hizmet Desteği yöneticisi rolünü atayın: <br> - Hizmet isteklerini açma yönetme <br> - Mesaj Merkezi yayınlarını görüntüleyin ve paylaşma <br> - Hizmet durumunu görüntüleme   |
|SharePoint yöneticisi    |   SharePoint Çevrimiçi yönetim merkezine erişmesi ve yönetmesi gereken kullanıcılara SharePoint yönetici rolünü atayın. <br><br>SharePoint yöneticileri şunları yapabilir: <br> - Site oluşturma ve silme <br> - Site koleksiyonları ve genel SharePoint ayarlarını yönetme   |
|Teams yöneticisi    |   Teams yönetim merkezine erişmesi ve bu merkezi yönetmesi gereken kullanıcılara Teams yöneticisi rolünü atayın. <br><br>Teams yöneticisi aynı zamanda şunları da yapabilir: <br> - Toplantıları yönetme <br> - Konferans köprülerini yönetme <br> - Bütün kuruluş geneli, federasyon, ekipler yükseltme, ve ekipler istemci ayarlarını da içeren ayarları yönetme   |
|Kullanıcı yöneticisi     |    Aşağıdaki işlemi yapmasına gerek duyan kullanıcılara Kullanıcı yöneticisi rolünü atayın: <br> - Kullanıcı ve grup ekleme <br> - Lisans atama <br> - Birçok kullanıcı özelliğini yönetme <br> - Kullanıcı görşleri oluşturma ve yönetme <br> - Parola zamanı geçme ilkelerini güncelleme <br> - Hizmet isteklerini yönetme  <br> - Hizmet durumunu görüntüleme <br><br>  Kullanıcı Yöneticisi, yöneticileri olmayan kullanıcılar için ve aşağıdaki rollere atanan kullanıcılar için aynı zamanda aşağıdaki eylemleri de yapabilir: Dizin gözetmeni, Konuk davetleri, Yardım masası yöneticisi, İleti merkezi gözetmeni, Rapor gözetmeni: <br> -Kullanıcı adlarını yönetme<br> - Kullanıcı silme ve geri yükleme<br> - Parolaları sıfırlama <br> - Kullanıcıları oturumu kapatmaya zorlama <br> - (FIDO) cihaz anahtarlarını güncelleme   |

## <a name="delegated-administration-for-microsoft-partners"></a>Microsoft İş ortakları için temsilci yönetim

Bir Microsoft iş ortağıyla çalışıyorsanız, onlara yönetici rolleri atayabilirsiniz. Onlar da şirketinizdeki kullanıcılara veya şirketlerine yönetici rolleri atayabilir. Örneğin, çevrimiçi organizasyonunuzu sizin için ayarlayıp yönetiyorlarsa, bunu yapmalarını isteyebilirsiniz.
  
Bir iş ortağı şu rolleri atayabilir: 
  
- İş Ortağı Merkezi aracılığıyla çok faktörlü kimlik doğrulamasını yönetmek dışında, genel bir yöneticiye eşdeğer **Yönetici Temsilcisi** Ayrıcalıkları.

- Bir yardım masası yöneticisine eşdeğer **Yardım Masası Temsilcisi** Ayrıcalıkları.

İş ortağının kullanıcılara bu rolleri atamadan önce, iş ortağını hesabınıza yönetici temsilcisi olarak eklemeniz gerekir. Bu süreç yetkili bir iş ortağı tarafından başlatılır. İş ortağı, kendisine yönetici temsilcisi olarak hareket etme izni vermek isteyip istemediğinizi sormak için size bir e-posta gönderir. Yönergeler için bkz. [İş ortağı ilişkilerini yetkilendirme veya kaldırma](../misc/add-partner.md).
  
## <a name="related-content"></a>İlgili içerik

[Yönetici rollerini atama](assign-admin-roles.md) (makale)\
[Microsoft 365 yönetim merkezindeki Azure AD rolleri](azure-ad-roles-in-the-mac.md) (makale)\
[Microsoft 365 yönetim merkezindeki etkinlik raporları](../activity-reports/activity-reports.md) (makale)\
[Exchange Online yönetici rolü](about-exchange-online-admin-role.md) (makale)
