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
description: Hizmet yöneticisi gibi yönetici rolleri iş işlevleriyle eşler ve yönetim merkezinde belirli görevleri gerçekleştirme izinleri sağlar.
ms.openlocfilehash: 5bea496ca24f3aef97a780d48c74b84aaa46176b
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "62973891"
---
# <a name="about-admin-roles"></a>Yönetici rolleri hakkında

Microsoft 365 veya Office 365, bir dizi yönetici rolüyle gelir ve bu rolleri kullanarak kuruluşta kullanıcılara <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a>. Her bir yönetici rolü, işletme ile ilgili genel işlevlere yöneliktir ve kuruluşunuzdaki kişilere, yönetim merkezlerinde belirli görevler yapma izni verir.

Bu <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a>, Azure AD rollerini ve kullanıcı rollerini yönetmenize Microsoft Intune sağlar. Bununla birlikte, bu roller Azure AD portalında ve Intune yönetim merkezinde kullanılabilen rollerin bir alt kümesidir.

> [!TIP]
> Bu konudaki adımlarda yardıma ihtiyacınız varsa, [Microsoft küçük işletme uzmanıyla çalışmayı göz önünde bulundurabilirsiniz](https://go.microsoft.com/fwlink/?linkid=2186871). İş Yardımı ile, işe alımtan günlük kullanıma kadar işlerinizi büyüttükçe siz ve çalışanlarınız küçük işletme uzmanlarına 24 saat erişim elde ediyor.

## <a name="watch-what-is-an-admin"></a>İzle: Yönetici nedir?

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1SRc0]

1. E-Microsoft 365, uygulama başlatıcıyı seçin. Yönetici düğmesini görüyorsanız, o zaman yöneticisinizdir.
1. Diğer **seçeneklere** gitmek için Yönetici'Microsoft 365 yönetim merkezi.
1. Sol gezinti bölmesinde **UsersActive** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**users öğesini seçin**</a>.
1. Yönetici yapmak istediğiniz kişiyi seçin. Kullanıcının ayrıntıları doğru iletişim kutusunda görüntülenir.

## <a name="before-you-begin"></a>Başlamadan önce

Kısa süre içinde yönetebilirsiniz ayrıntılı Azure AD rol açıklamalarının tam listesini <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a>? [Azure Active Directory'de yönetici rolü izinleri[’ne göz atın. [Azure AD yerleşik rolleri](/azure/active-directory/roles/permissions-reference).

Kısa süre içinde yönetebilirsiniz ayrıntılı Intune rol açıklamalarının tam <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">listesini Microsoft 365 yönetim merkezi?</a>  Daha fazla [bilgi için Rol tabanlı erişim denetimi (RBAC) Microsoft Intune](/mem/intune/fundamentals/role-based-access-control).

Kaynakta rol atama hakkında daha fazla bilgi <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> bkz[. Yönetici rolleri atama](assign-admin-roles.md).

## <a name="security-guidelines-for-assigning-roles"></a>Rolleri atamayla ilgili güvenlik yönergeleri

Yöneticilerin hassas verilere ve dosyalara erişimi olduğundan, kuruluşunuzun verilerinin daha güvenli kalması için bu yönergeleri izlemenizi öneririz.

| Öneri                  | Bu neden önemlidir?                 |
| :------------------- | :------------------- |
| 2 ila 4 arasında genel yönetici belirleyin  | Bir genel yönetici parolasını yalnızca başka bir genel yönetici sıfırlayabileceği için, hesap kilitlenmesi durumunda kuruluşunuzda en az 2 genel yönetici bulundurmanızı öneririz. Ancak genel yönetici, kuruluşunuzun ayarlarına ve verilerin çoğuna neredeyse sınırsız erişime sahiptir, bu nedenle 4 ' ten fazla genel yönetici bulundurmamanızı öneririz, çünkü bu bir güvenlik tehdidi olur. |
| *En az izin verilen* rolü atama    | *En az izin verilen* rolün atanması, yöneticilere yalnızca işin yapılmasını sağlamak için gereken erişimi verme anlamına gelir. Örneğin, bir kişinin çalışan parolalarını sıfırlamasını istiyorsanız, sınırsız genel yönetici rolünü atamamalısınız, parola Yöneticisi veya Yardım Masası Yöneticisi gibi sınırlı bir yönetim rolü atamalısınız. Bu, verilerinizin güvenliğini korumaya yardımcı olur.                 |
| Yöneticiler için çok faktörlü kimlik doğrulaması gerektirme                  |    Kullanıcılarınızın tüm kullanıcılarınız için ÇFKD gerektirmek iyi bir fikirdir olsa da, yöneticilerin kesinlikle giriş yapmak için ÇFKD kullanması gerekmelidir. ÇFKD, kullanıcıların söyledikleri kişi olduklarını doğrulayacak ikinci bir doğrulama yöntemi girmesini sağlar. Yöneticiler çok sayıda müşteri ve çalışan verilerine erişebilir ve ÇFKD gerektirirseniz, yöneticinin parolasının tehlikeye düşmesi durumunda bile parola, ikinci doğrulama yöntemi olmadan işlevsiz olur.  <br><br>ÇFKD'yi açtığınızda, kullanıcının bir dahaki sefer oturum açtığında hesap kurtarma için alternatif bir e-posta adresi ve telefon numarası sağlaması gerekecektir.  <br> [Çok faktörlü kimlik doğrulamasını ayarlama](../security-and-compliance/set-up-multi-factor-authentication.md)          |

Yönetim merkezinde bir veya daha fazla sayfa düzenleme izniniz olmadığını söyleyen bir ileti alırsanız, bunun nedeni o izne sahip olmayan bir rol atamanız olabilir.

## <a name="commonly-used-microsoft-365-admin-center-roles"></a>Yaygın olarak kullanılan Microsoft 365 yönetim merkezi rollerini

Ayrıntılar Microsoft 365 yönetim merkezi, Rol <a href="https://go.microsoft.com/fwlink/p/?linkid=2097861" target="_blank">**atamaları'ne gidip**</a> herhangi bir rolü seçerek ayrıntı bölmesini açabilirsiniz. Bu **rolü ataan** yöneticilerin yapma iznine sahip olduğu yöneticilerin ayrıntılı listesini görüntülemek için İzinler sekmesini seçin. Atanan **veya Atanan** yöneticiler **sekmesini seçerek** kullanıcıları rollere ekleyin.

Muhtemelen kuruluşunuzda yalnızca aşağıdaki rolleri atamanız gerekecek. Varsayılan olarak öncelikle, çoğu kuruluşun kullandığı rolleri gösteririz. Bir rol bulamazsanız, listenin en altına gidin ve Tüm kategoriye göre **göster'i seçin**. (Bir rolle ilişkili cmdlet'ler de dahil olmak üzere ayrıntılı bilgi için bkz. [Azure AD yerleşik rolleri](/azure/active-directory/roles/permissions-reference).)

|Yönetici rolü     |Bu role kim atanmalıdır?  |
|---------|---------|
|Faturalama yöneticisi     |   Satın alma yapan, abonelikleri ve hizmet isteklerini yöneten ve hizmet durumunu takip eden kullanıcılara Faturalama yöneticisi rolü attayabilirsiniz. <br><br> Faturalama yöneticileri ayrıca şunları da olabilir:<br> - Faturalandırmayı her açıdan yönetin <br> - Azure portalda destek biletlerini oluşturun ve yönetin <br>  |
|Exchange yöneticisi     |   Kullanıcı Exchange posta kutularını, kullanıcı gruplarını ve diğer kullanıcı gruplarını görüntülemesi ve yönetmesi gereken kullanıcılara Microsoft 365 yönetici Exchange Online. <br><br> Exchange yöneticileri aynı zamanda şunları da yapabilir:<br> - Bir kullanıcının posta kutusundaki silinen öğeleri kurtarma <br> -"Olarak Gönder" ve "Adına gönder" temsilcilerini ayarlama <br>  |
|Genel yönetici     |   Genel yönetici rolünü, Microsoft çevrimiçi hizmetlerindeki çoğu yönetim özellikleri ve verilere ulaşması gereken kullanıcılara atayın. <br><br> Gereğinden fazla sayıda kullanıcıya genel erişim vermek bir güvenlik riskidir ve 2 ila 4 arasında Genel yönetici belirlemenizi tavsiye ediyoruz. <br><br> Sadece genel yöneticiler şunları yapabilir:<br> - Tüm kullanıcılar için parola sıfırlama <br> - Etki alanları ekleme ve yönetme <br> - Başka bir genel yöneticinin engellemesini kaldırma <br> <br> **Not:**   Microsoft çevrimiçi hizmetler’e kaydolan kullanıcı otomatik olarak genel yönetici olur. |
|Genel gözetmen    |   Genel bir yöneticinin görüntüleyebileceği yönetim merkezlerinde yönetici özelliklerini ve ayarlarını görüntülemesine gerek duyan kullanıcılara genel gözetmen rolü atayın. Genel gözetmen yönetici hiçbir ayarı düzenleyemez.   |
|Gruplar yöneticisi     |   Grup yöneticisi rolünü, portal ve portal dahil olmak üzere yönetim merkezleri genelinde tüm grup ayarlarını yönetmesi Microsoft 365 yönetim merkezi Azure Active Directory attayabilirsiniz. <br><br> Grup yöneticileri şunları yapabilir:<br> - Grup oluşturma, düzenleme, silme ve Microsoft 365 geri yükleme <br> -Grup oluşturma, süre sonu ve adlandırma ilkeleri oluşturma ve güncelleştirme <br> -Azure Active Directory güvenlik gruplarını oluşturma, düzenleme, silme ve geri yükleme| 
|Yardım Masası Yöneticisi     |   Aşağıdaki işlemi yapmasına gerek duyan kullanıcılara yardım masası yönetici rolünü atayın:<br> - Parolaları sıfırlama <br> - Kullanıcıları oturumu kapatmaya zorlama <br> - Hizmet isteklerini yönetme  <br> - Hizmet durumunu görüntüleme <br> <br> **Not**: Yardım Masası Yöneticisi yalnızca yönetici olmayan kullanıcılara ve kullanıcılara şu rollere sahip olmak için yardım edebilir: Dizin gözetmeni, Konuk davetli, Yardım masası Yöneticisi, İleti merkezi gözetmeni ve Rapor gözetmeni.      |
|Lisans yöneticisi    |   Kullanıcılara lisans ataması ve kaldırması ve kullanım konumlarını düzenlemesi gereken kullanıcılara Lisans yöneticisi rolü attayabilirsiniz. <br/><br/> Lisans yöneticileri ayrıca şunları da şunları da olabilir: <br> - Grup tabanlı lisanslama için lisans atamalarını yeniden işleme <br> - Grup tabanlı lisanslama için gruplara ürün lisansları atama  |
|Office Uygulamaları yöneticisi    |   Aşağıdaki işlemi yapmasına gerek duyan kullanıcılara Office Uygulamaları yöneticisi rolünü atayın: <br> -Office bulut ilkesi hizmetini kullanarak Office için bulut tabanlı ilkeler oluşturma ve yönetme <br> - Hizmet istekleri oluşturma ve yönetme <br> - Kullanıcıların kendi uygulamalarında göreceği Yeni Office yönetme   <br> - Hizmet durumunu görüntüleme  |
|Parola yöneticisi  |   Yönetici olmayanların ve Parola Yöneticilerinin parolalarını sıfırlaması gereken bir kullanıcıya Parola yöneticisi rolünü atlayın.   |
|Message merkezi gözetmeni |   İleti merkezi okuyucu rolünü, şunları yapacak kullanıcılara attayabilirsiniz: <br> - İleti merkezi bildirimlerini izleme <br> - İleti merkezi gönderileri ve güncelleştirmelerinin haftalık e-posta özetlerini alın <br> - İleti merkezi gönderilerini paylaşma <br> - Kullanıcılar ve gruplar gibi Azure AD hizmetleri için salt okunur erişime sahip olmak|
|Power Platform yöneticisi |   Power Platform yönetici rolünü, şunları yapacak kullanıcılara attayın: <br> - Veri kaybı önleme Power Apps, Power Automate için tüm yönetici özelliklerini yönetme <br> - Hizmet istekleri oluşturma ve yönetme <br> - Hizmet durumunu görüntüleme  |
|Rapor gözetmeni |   Aşağıdakileri yapmaları gereken kullanıcılara Raporlar okuyucu rolü attayabilirsiniz: <br> - Etkinlik verilerini ve etkinlik raporlarını çalışma Microsoft 365 yönetim merkezi <br> - Benimseme içerik paketine Power BI erişin <br> - Azure AD'de oturum açma raporlarına ve etkinliklerine erişim elde edin <br> - Microsoft Graph raporlama API'si tarafından döndürülen verileri görüntüleme|
|Hizmet Desteği yöneticisi   |   Her zamanki yönetici rollerine ek olarak, şunları yapmaları gereken yöneticilere veya kullanıcılara ek bir rol olarak Hizmet Desteği yönetici rolünü attayabilirsiniz: <br> - Hizmet isteklerini açma yönetme <br> - Mesaj Merkezi yayınlarını görüntüleyin ve paylaşma <br> - Hizmet durumunu görüntüleme   |
|SharePoint yöneticisi    |   SharePoint Çevrimiçi yönetim merkezine erişmesi ve yönetmesi gereken kullanıcılara SharePoint yönetici rolünü atayın. <br><br>SharePoint yöneticileri şunları yapabilir: <br> - Site oluşturma ve silme <br> - Site koleksiyonları ve genel SharePoint ayarlarını yönetme   |
|Teams yönetici    |   Yönetim Teams erişmesi ve yönetmesi gereken kullanıcılara yönetici rolü Teams attayabilirsiniz. <br><br>Teams yönetici şunları da olabilir: <br> - Toplantıları yönetme <br> - Konferans köprülerini yönetme <br> - Bütün kuruluş geneli, federasyon, ekipler yükseltme, ve ekipler istemci ayarlarını da içeren ayarları yönetme   |
|Kullanıcı yöneticisi     |    Aşağıdaki işlemi yapmasına gerek duyan kullanıcılara Kullanıcı yöneticisi rolünü atayın: <br> - Kullanıcı ve grup ekleme <br> - Lisans atama <br> - Birçok kullanıcı özelliğini yönetme <br> - Kullanıcı görşleri oluşturma ve yönetme <br> - Parola zamanı geçme ilkelerini güncelleme <br> - Hizmet isteklerini yönetme  <br> - Hizmet durumunu görüntüleme <br><br>  Kullanıcı Yöneticisi, yöneticileri olmayan kullanıcılar için ve aşağıdaki rollere atanan kullanıcılar için aynı zamanda aşağıdaki eylemleri de yapabilir: Dizin gözetmeni, Konuk davetleri, Yardım masası yöneticisi, İleti merkezi gözetmeni, Rapor gözetmeni: <br> -Kullanıcı adlarını yönetme<br> - Kullanıcı silme ve geri yükleme<br> - Parolaları sıfırlama <br> - Kullanıcıları oturumu kapatmaya zorlama <br> - (FIDO) cihaz anahtarlarını güncelleme   |

## <a name="delegated-administration-for-microsoft-partners"></a>Microsoft İş ortakları için temsilci yönetim

Bir Microsoft iş ortağıyla çalışıyorsanız, iş ortağınız için yönetici rolleri atayabilirsiniz. Bu yöneticiler de sizin şirketiniz veya şirket yöneticileri için kullanıcılar atayın. Örneğin bunu, sizin için çevrimiçi kuruluşunuzu oluşturup yönetecekse iş ortağınıza yönetici rolü atamak isteyebilirsiniz.
  
Bir iş ortağı şu rolleri atayabilir: 
  
- **Yönetici Temsilcisi** İş Ortağı Merkezi aracılığıyla çok faktörlü kimlik doğrulamasını yönetme dışında, genel yöneticiye eşdeğer ayrıcalıklar.

- **Yardım masası Aracısı** Yardım masası yöneticisine eşdeğer ayrıcalıklar.

İş ortağı bu rolleri kullanıcılara atamadan önce, iş ortağını hesabınıza temsili yönetici olarak eklemeniz gerekir. Bu işlem, yetkili bir iş ortağı tarafından başlatılır. İş ortağı size bir e-posta göndererek size yönetici temsilcisi olarak görev yapma izni vermek isteyip istemediğinizi sorar. Yönergeler için, bkz. [İş ortağı ilişkilerini yetkilendirme veya kaldırma](../misc/add-partner.md).
  
## <a name="related-content"></a>İlgili içerik

[Yönetici rollerini atama](assign-admin-roles.md) (makale)\
[Microsoft 365 yönetim merkezi Azure AD](azure-ad-roles-in-the-mac.md) rolleri (makale)\
[Etkinlik raporları Microsoft 365 yönetim merkezi](../activity-reports/activity-reports.md) (makale)\
[Exchange Online rolü (](about-exchange-online-admin-role.md)makale)
