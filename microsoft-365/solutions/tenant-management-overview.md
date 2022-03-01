---
title: Kurumsal kiracılar için Microsoft 365 yönetimi
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-tenantmanagement
- m365solution-overview
- tenant-management
ms.custom:
- Ent_Solutions
description: Kiracılarınızı planlamaya, dağıtmaya ve devam eden işlemlere Microsoft 365 genel bakış.
ms.openlocfilehash: 7a9545800c3f5f08b8094290c4173b4368caff4d
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/10/2022
ms.locfileid: "63011786"
---
# <a name="tenant-management-for-microsoft-365-for-enterprise"></a>Kurumsal kiracılar için Microsoft 365 yönetimi

Bulut bilgi işlem ile organizasyonlu dijital dönüşümüne bir yol oluşturmak, çalışanlarının üretkenlik, işbirliği, performans, gizlilik, uyumluluk ve güvenlikten güven güveneceği kesin bir temel gerektirir.

Kiracılar için doğru yapılandırma Microsoft 365 temel, çalışanlarınızı çalışmalarınızı yapmaları için ve IT departmanınızı ek iş değeri sağlayan  uç çözümlere odaklanmaya bırakarak bu temelin sağlar.

Bu çözüm, şu adımlarda temelin yapılandırmasında size yol gösterir:

1. Kiracılarınızı belirleme
2. Ağ için en iyi duruma getirme
3. Kimliklerinizi eşitleme ve güvenli oturum açmaları zorunlu hale uygulama
4. Windows cihazlarınızı, Office istemcilerinizi ve şirket içi sunucularınızı Office verileri geçirme
5. Cihaz ve uygulama yönetimini dağıtma

Ama ilk olarak, bir kiracının ne olduğunu ve firma temelini sağlayan bir kiracının nasıl göründüğünü anlamak için bir dakikanız var.

## <a name="a-microsoft-365-tenant-defined"></a>Tanımlanmış Microsoft 365 kiracı

Kiracı Microsoft 365, Avrupa veya Kuzey Amerika gibi belirli bir varsayılan konumda depolanan Microsoft 365 hizmetlerinizin ve kuruluş verilerinizin özel bir örneğidir. Bu konum, kiracıyı kurum için  oluşturmak üzere belirttiğinizde belirtilir. Her Microsoft 365 kiracı farklı, benzersiz ve diğer tüm kiracılardan Microsoft 365 olur. Microsoft'tan Microsoft 365 veya E5 gibi bir veya daha fazla ürün satın Microsoft 365 E3 ve her biri için bir lisans kümesi satın alan bir kiracı oluşturabilirsiniz.

Ayrıca Microsoft 365 kiracınız, Azure Active Directory hesapları, gruplar ve diğer nesneler için Azure AD'nin özel bir örneği olan bir Azure AD (Azure AD) kiracısı da içerir. Her Azure AD kiracısı, birbirinden ayrı, benzersiz ve diğer tüm Azure AD kiracılarından ayrıdır. Kurumda, Azure abonelikleriyle ayar kullanabileceğiniz birden çok Azure AD kiracısı olabilir, ancak Microsoft 365 kiracı, kiracıyı oluşturulduğunda oluşturulan tek bir Azure AD kiracısı kullanabilir.

İşte bir örnek:

![Kiracıya Microsoft 365 Azure AD kiracısına örnek.](../media/tenant-management-overview/tenant-management-example-tenant.png)

*Kiracı yönetimi*, kiracılarınızı planlama, dağıtım ve devam eden Microsoft 365 olur.

## <a name="attributes-of-a-well-designed-and-operating-tenant"></a>İyi tasarlanmış ve işletim kiracısı öznitelikleri

Kiracınız için doğru ad ve konumun ötesinde, Microsoft Teams ve Exchange Online&mdash; gibi bulut üretkenlik uygulamalarıyla kullanıcı deneyimlerinizi etkili,&mdash; güvenli ve performans sahibi olduğundan emin olmak için planlamanız, dağıtmanız ve yönetmeniz gereken ek öğeler de vardır.

Bu öğeler şöyledir:

- Doğru ürün (abonelik) ve lisans kümeniz var.
  - Ürün kümesi işletmeniz, IT ve güvenlik ihtiyaçlarını karşılar.
  - Çalışanlarınız için yeterli sayıda lisans var ve personel çalışmalarında beklenen değişiklikler var.
- Ağ için:
  - Doğru DNS etki alanı adlarını yapılandırdınız.
  - Kurumsal ağlar için, site içi çalışanlar için ağ trafiğini Microsoft ağına en iyi duruma gönderdiysiniz.
  - VPN istemcisi kullanan uzak çalışanlar için ağ trafiğini en iyi duruma kapattınız.
- Active Directory Etki Alanı Hizmetleri (AD DS) hesaplarınızı, gruplarınızı ve diğer nesneleri eşitleebilirsiniz.
  - Azure AD kiracı hesaplarınız, e-posta adresleri Exchange Online DNS etki alanlarına sahip posta kutularıyla eşlenmiştir.
  - Kullanıcı hesaplarınıza, satın alınan doğru ürünlerden (Microsoft 365 E3 E5 gibi) doğru lisanslar atandı.
- Güçlü kimlik ve erişim yönetimi yapılandırıldı.
  - Parolasız veya çok faktörlü kimlik doğrulamasıyla (MFA) güvenli kullanıcı oturum açmasını gerektirirsiniz.
  - Daha yüksek güvenlik düzeyleri için oturum açma gereksinimlerini ve kısıtlamaları zorunlu bulunduran Koşullu Erişim ilkeleriniz vardır.
- Şirket içi Office sunucuları ve verileri bulut uygulamalarına geçirildi veya karma bir yapılandırmada kullanılıyor.
- Yerleşik Intune veya Temel Mobil Kullanım ve Güvenlik ile cihaz yönetimini Microsoft 365.
  - Kuruluşa ait cihazlarınız kaydedildi ve yönetilir.
  - Kişisel cihazlar için uygulamalar yönetilir.

Burada, tüm bu öğelerin Microsoft 365 bir kiracının yer alan bir örneği ve ve bir örneği yer alıyor.

![Kiracıya Microsoft 365.](../media/tenant-management-overview/tenant-management-tenant-config.png)

Bu çizimde, kiracıya Microsoft 365 içerir:

- Ürünler ve E5 lisansları Microsoft 365 E3 lisansları.
- Microsoft 365 uygulamalarınızı oluşturun.
- Kayıtlı cihazlarla cihaz ve uygulama ilkeleriyle Intune.
- Eşitlenmiş kullanıcı hesabı (gruplar ve diğer dizin nesneleri gösterilmez), etki alanları ve Koşullu Erişim ilkelerine sahip bir Azure AD kiracısı.

## <a name="tenant-capabilities-for-microsoft-365-for-enterprise"></a>Kurumsal kiracılar için Microsoft 365 özellikleri

Aşağıdaki bölümlerde ve tabloda, bu çözümde yer alan adımlara uygulanacak temel özellikler ve lisanslama listelanmaktadır.

### <a name="tenant"></a>Kiracı

|Özellik veya özellik|Açıklama|Lisanslama|
|---|---|---|
|Birden çok kiracı|Her Microsoft 365 kiracı farklı, benzersiz ve diğer tüm kiracılardan Microsoft 365 olur. Birden çok kiracıyla, bunları yönetme ve kullanıcılarınıza hizmet sağlama konusunda kısıtlamalar ve dikkate alınması gereken başka noktalar vardır.|Microsoft 365 E3 E5|
|Kiracılar arası posta kutusu geçişi|Kiracı yöneticileri, şirket içi sistemlerinde en düşük altyapı bağımlılıkları olan posta kutularını kiracılar arasında hareket ettirebilirsiniz. Bu işlem, alan dışı posta kutuları ve ekleme ihtiyacı ortadan kaldırır.|Microsoft 365 E3 E5|
|Multi-Geo|Kiracınız, veri yerleşim gereksinimlerini karşılamayı seçtiğiniz diğer veri merkezi coğrafi konumlarında rest rest konumunu depolar.|Microsoft 365 E3 E5|
|Temel verileri yeni bir veri merkezi coğrafi olarak taşıma|Microsoft ek kapasite ve bilgi işlem kaynakları için yeni veri merkezi coğrafi olarak ekley isteğinde bulundurarak, çekirdek müşteri verileriniz için bir veri merkezi coğrafi olarak taşınmasını talep edilebilir.|Microsoft 365 E3 E5|
||||

### <a name="networking"></a>Ağ

|Özellik veya özellik|Açıklama|Lisanslama|
|---|---|---|
|Ağ Analizler|Office konumlar için ağ Microsoft 365 tasarlamanıza yardımcı olmak için kiracı kiracınız tarafından toplanan ağ performansı ölçümleri.|Microsoft 365 E3 E5|
|Uç nokta güncelleştirmelerini otomatikleştirme|İstemci PAC dosyalarınız, ağ cihazlarınız ve Microsoft 365 hizmetlerinizin tüm uç noktaları için yapılandırmasını ve devam eden güncelleştirmeleri otomatikleştirin.|Microsoft 365 E3 E5|
||||

### <a name="identity"></a>Kimlik

|Özellik veya özellik|Açıklama|Lisanslama|
|---|---|---|
|Şirket içi Active Directory Etki Alanı Hizmetleri'i (AD DS) Azure AD kiracınız ile eşitleme|Kullanıcı hesapları, gruplar ve diğer nesneler için şirket içi kimlik sağlayıcınızdan faydalanın.|Microsoft 365 E3 E5|
|Güvenlik varsayılanları ile zorunlu kılınan MFA|Oturum açma işlemleri için ikinci bir kimlik doğrulama biçimi gerektirerek güvenliği tehlikeye atılmış kimliklere ve cihazlara karşı koruyun. Güvenlik varsayılanları, tüm kullanıcı hesapları için MFA gerektirir.|Microsoft 365 E3 E5|
|Koşullu Erişim ile zorunlu kılınan MFA|Koşullu Erişim ilkeleriyle oturum açma özniteliklerini temel alarak MFA gerektirme.|Microsoft 365 E3 E5|
|Risk tabanlı Koşullu Erişim ile zorunlu kılınan MFA|Kullanıcının Kimlik için Microsoft Defender ile oturum açma riski temel alarak MFA gerektirme.|Microsoft 365 E5 lisansları olan E3 Azure AD Premium P2 E3|
|Self-Service Sıfırlama (SSPR)|Kullanıcılarının parolalarını veya hesaplarını sıfırlamasına veya kilidini açmasına izin ver.|Microsoft 365 E3 E5|
||||

### <a name="migration"></a>Geçiş

|Özellik veya özellik|Açıklama|Lisanslama|
|---|---|---|
|Geçiş Windows 10|7 veya 12 Windows çalıştıracak Windows 8.1 cihazlarınızı Windows 10 Enterprise.|Windows 10 Enterprise veya E5'e dahil Microsoft 365 E3 lisansları|
|Geçiş Kurumlar için Microsoft 365 Uygulamaları|Word Office ve PowerPoint gibi istemci uygulamalarınızı buluttan yeni özelliklerle güncelleştirilen sürümlere geçirme.|Microsoft 365 E3 E5|
|Şirket içi sunucuları ve verileri başka sunuculara Microsoft 365|Paylaşılan posta Exchange, sitelerinizi SharePoint ve Skype Kurumsal Online'Microsoft 365 geçirebilirsiniz.|Microsoft 365 E3 E5|
||||

### <a name="device-and-app-management"></a>Cihaz ve uygulama yönetimi

|Özellik veya özellik|Açıklama|Lisanslama|
|---|---|---|
|Microsoft Intune|Cep telefonları, tabletler ve dizüstü bilgisayarlar dahil olmak üzere kuruluş uygulamanın ve cihazların nasıl kullanlıklarını denetlemeniz için mobil cihaz yönetimi (MDM) ve mobil uygulama yönetimi (MAM) sağlayan bulut tabanlı bir hizmet.|Microsoft 365 E3 E5|
|Temel Hareketlilik ve Güvenlik|Bu yerleşik hizmetle kullanıcılarının iPhone, iPad, Android ve Windows mobil cihazlarının güvenliğini sağlama ve yönetme.|Microsoft 365 E3 E5|
||||

## <a name="next-steps"></a>Sonraki adımlar

Kiracılarınızı ayarlamak ve yönetmek için bu Microsoft 365 kullanın.

1. [Kiracılarınızı belirleme](tenant-management-tenants.md)
2. [Ağ için en iyi duruma getirme](tenant-management-networking.md)
3. [Kimliklerinizi eşitleme ve güvenli oturum açmaları zorunlu hale uygulama](tenant-management-identity.md)
4. [Şirket içi veri sunucularınızı Office verileri geçirme](tenant-management-migration.md)
5. [Cihaz ve uygulama yönetimini dağıtma](tenant-management-device-management.md)

[![Kiracıyı dağıtma ve yönetme Microsoft 365.](../media/tenant-management-overview/tenant-management-step-grid.png)](tenant-management-tenants.md)

Her adım dağıtım seçeneklerini açıklar, sonuçları ve sürekli bakım görevlerini özetler.

Kendi kiracılarının öğelerini nasıl kurgusal ama temsili bir çok uluslu kuruluşun farklı bir kiracıya Microsoft 365 olduğunu anlamak için[, Contoso örnek olay incelemesini incelenin](../enterprise/contoso-case-study.md).
