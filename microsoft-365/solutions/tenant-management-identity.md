---
title: Adım 3. Kurumsal kiracılar için Microsoft 365 kimlik
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
- tenant-management
- m365solution-scenario
ms.custom:
- Ent_Solutions
description: Kiracınız için doğru kimlik modelini Microsoft 365 güçlü kullanıcı oturum açmalarını zorunlu kılın.
ms.openlocfilehash: cb57b62f18afcd669b3dd84c25096e5dd72b25d0
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/10/2022
ms.locfileid: "63027588"
---
# <a name="step-3-identity-for-your-microsoft-365-for-enterprise-tenants"></a>Adım 3. Kurumsal kiracılar için Microsoft 365 kimlik

Sizin Microsoft 365 kiracınız, oturum Azure Active Directory kimliklerini ve kimlik doğrulamasını yönetecek bir Kullanıcı Adı (Azure AD) kiracısı içerir. Kimlik altyapınızı doğru şekilde yapılandırmak, kullanıcıların erişimini Microsoft 365 izinlerini yönetme açısından çok önemlidir.

## <a name="cloud-only-vs-hybrid"></a>Yalnızca bulut ve karma karşılaştırması

İki tür kimlik modeli ve bunların en uygun ve avantajları aşağıdaki gibidir.


| Model | Açıklama | Kullanıcı Microsoft 365 kimlik doğrulaması nasıl olur? | En iyi | En büyük avantaj |
|:-------|:-----|:-----|:-----|:-----|
| Yalnızca bulut | Kullanıcı hesabı, kiracınız için yalnızca Azure AD Microsoft 365 vardır. | Kiracınız için Azure AD kiracısı Microsoft 365 kimlik doğrulamasını bulut kimliği hesabıyla gerçekleştirir. | Şirket içi Active Directory'si olmayan veya buna gerek olmayan kuruluşlar. | Kullanımı kolaydır. Fazladan dizin aracı veya sunucu gerekmez. |
| Karma |  Kullanıcı hesabı şirket içi Active Directory Etki Alanı Hizmetleri'niz (AD DS) içinde yer alır ve bu hesabın bir kopyası da etki alanı kiracınız için Azure AD Microsoft 365 bulunur. Azure AD Bağlan, Azure AD kiracınıza AD DS değişikliklerini eşitlemek için şirket içi bir sunucuda çalışır. Azure AD'de kullanıcı hesabı, zaten karma olarak karma olarak karma bir AD DS kullanıcı hesabı parolasının karma sürümünü de içerebilir. | Kiracınız için Azure AD kiracısı Microsoft 365 kimlik doğrulama işlemini ele alır veya kullanıcıyı başka bir kimlik sağlayıcısına yeniden yönlendirebilir. | AD DS veya başka bir kimlik sağlayıcısı kullanan kuruluşlar. | Kullanıcılar, şirket içi veya bulut tabanlı kaynaklara erişirken aynı kimlik bilgilerini kullanabilir. |
||||||

Burada, yalnızca bulut kimliğinin temel bileşenleri ve bilgileri ve bilgileri ve hizmetleri ve diğer bileşenleri ve daha sonralarını açıklarız.

![Yalnızca bulut kimliğinin temel bileşenleri.](../media/about-microsoft-365-identity/cloud-only-identity.png)

Bu çizimde, şirket içi ve uzak kullanıcılar kendi kiracılarının Azure AD kiracısı hesaplarıyla oturum Microsoft 365 vardır.

Karma kimliğin temel bileşenleri aşağıdaki gibidir.

![Karma kimliğin temel bileşenleri.](../media/about-microsoft-365-identity/hybrid-identity.png)

Bu çizimde, şirket içi ve uzak kullanıcılar, şirket içi AD DS'lerinden kopyalanmış olan Azure AD kiracısı hesaplarıyla kendi Microsoft 365 kiracılarında oturum gösterir.

## <a name="synchronizing-your-on-premises-ad-ds"></a>Şirket içi AD DS'nizi eşitleme

İş gereksinimlerinize ve teknik gereksinimlerinize bağlı olarak, karma kimlik modeli ve dizin eşitlemesi, kurumsal müşterileri benimsemek için en yaygın Microsoft 365. Dizin eşitlemesi, AD DS'niz içinde kimlikleri yönetmenize olanak sağlar ve kullanıcı hesapları, gruplar ve kişilerde yapılan tüm güncelleştirmeler, kullanıcı ad kiracınıza bağlı Azure AD kiracıyla Microsoft 365 eşitlenir.

> [!NOTE]
> AD DS kullanıcı hesapları ilk kez eşitlenirken, bu hesaplara otomatik olarak Microsoft 365 lisansı atanamaz ve e-Microsoft 365 hizmetlere erişamaz. Öncelikle onlara bir kullanım konumu atamalısiniz. Ardından, bu kullanıcı hesaplarına tek tek veya grup üyeliği aracılığıyla dinamik olarak lisans attayabilirsiniz.

Karma kimlik modelini kullanırken iki kimlik doğrulama türü şu şekildedir.

| Kimlik doğrulama türü | Açıklama |
|:-------|:-----|
| Yönetilen kimlik doğrulaması | Azure AD, parolanın yerel olarak depolanan karma sürümünü kullanarak kimlik doğrulama işlemini ele alır veya kimlik bilgilerini şirket içi AD DS tarafından kimlik doğrulaması yapılan bir şirket içi yazılım aracısına gönderir. <br> <br>  İki tür yönetilen kimlik doğrulaması vardır: Parola karması eşitlemesi (PHS) ve Geçişli kimlik doğrulaması (PTA). PHS ile, Azure AD kimlik doğrulamayı kendisine gerçekleştirir. PTA ile, Azure AD'nin kimlik doğrulamayı gerçekleştirmesi için AD DS'ye sahip olur. |
| Federasyon kimlik doğrulaması | Azure AD, kimlik doğrulaması talep etmek için istemci bilgisayarı başka bir kimlik sağlayıcısına yeniden yönlendirmektedir. |
|  |  |

Daha [fazla bilgi edinmek için bkz. doğru](/azure/active-directory/hybrid/choose-ad-authn) kimlik doğrulama yöntemini seçme.

## <a name="enforcing-strong-sign-ins"></a>Güçlü oturum açmaları zorlama

Kullanıcı oturum açmalarının güvenliğini artırmak için, aşağıdaki tabloda yer alan özellik ve özellikleri kullanın.

| Özellik | Açıklama | Daha fazla bilgi | Lisans gereksinimleri |
|:-------|:-----|:-----|:-----|:-----|
| Windows Hello Kurumsal | Bir cihazda oturum aken parolaları güçlü iki faktörlü kimlik doğrulamasıyla Windows değiştirir. Bu iki etmen bir cihaza bağlı olan yeni bir kullanıcı kimlik bilgileri türü ve bir biyometrik veya PIN'tir. | [Windows Hello Kurumsal'a Genel Bakış](/windows/security/identity-protection/hello-for-business/hello-overview) | Microsoft 365 E3 E5 |
| Azure AD Parola Koruması | Bilinen zayıf parolaları ve değişkenlerini algılar ve engeller; ayrıca, organizasyonuma özgü ek zayıf terimleri de engelleyebilir. | [Azure AD parola korumasını yapılandırma](/azure/active-directory/authentication/concept-password-ban-bad) | Microsoft 365 E3 E5 |
| Çok faktörlü kimlik doğrulamasını (MFA) kullanma | MFA, kullanıcı oturum açma işlemlerinin, akıllı telefon uygulaması ile doğrulama veya akıllı telefona gönderilen KıSA mesaj gibi kullanıcı hesabı parolasının ötesinde başka bir doğrulamaya tabi olması gerekir. Kullanıcıların [MFA'nın](https://support.microsoft.com/office/set-up-multi-factor-authentication-in-microsoft-365-business-a32541df-079c-420d-9395-9d59354f7225) nasıl ayarlandısı ile ilgili yönergeler için bu videoyu izleyin. | [Kurumsal için Microsoft 365 MFA](../enterprise/microsoft-365-secure-sign-in.md#mfa) | Microsoft 365 E3 E5 |
| Kimlik ve cihaz erişimi yapılandırmaları | Ayarlar önkoşul özellikleri ve ayarlarıyla Koşullu Erişim, Intune ve Azure AD Kimlik Koruması ilkeleriyle bir araya gelen ve belirli bir erişim isteğinin hangi koşullar altında verilmesi gerektiğini belirleyen ilkeler ve ilkeler.  | [Kimlik ve cihaz erişimi yapılandırmaları](../security/office-365-security/microsoft-365-policies-configurations.md) | Microsoft 365 E3 E5 |
| Azure AD Identity Protection | Bir saldırganın, kuruluşun bulut hizmetlerine ve verilerine erişmek için kullanıcının hesap adını ve parolasını belirlemesi ve kimlik bilgilerinin güvenliğinin tehlikeye atabilmesini sağlar. | [Azure AD Identity Protection](/azure/active-directory/active-directory-identityprotection) | Microsoft 365 E5 koruma Microsoft 365 E3 kimliği ile & veya kimlik doğrulama |
|  |  |  |



## <a name="results-of-step-3"></a>Adım 3'in sonuçları

Kiracınız için kimlik Microsoft 365, belirlediniz:

- Hangi kimlik modelinin kullanımı gerekir.
- Güçlü kullanıcı ve cihaz erişimini nasıl zorunlu kılınacak?

Yeni karma kimlik öğelerinin vurgulu olduğu bir kiracıya örnek olarak aşağıdaki örnek ve şekildedir.

![Kiracı için karma kimlik örneği.](../media/tenant-management-overview/tenant-management-tenant-build-step3.png)

Bu çizimde, kiracının sahip olduğu:

- Dizin eşitleme sunucusu ve Azure AD kiracısı kullanılarak Azure AD kiracısı ile eşitlenen bir AD DS ormanı Bağlan.
- AD DS kullanıcı hesaplarının ve ad DS ormanındaki diğer nesnelerin kopyası.
- Kullanıcı hesabına dayalı olarak güvenli kullanıcı oturum açmalarını ve erişimi zorunlu kılınan bir dizi Koşullu Erişim ilkesi.

## <a name="ongoing-maintenance-for-identity"></a>Kimlik için sürekli bakım

Sürekli olarak şunları yapmak zorundayabilirsiniz:

- Kullanıcı hesapları ve grupları ekleme veya değiştirme. Yalnızca bulut kimlikleri için, bulut tabanlı kullanıcılarınızı ve gruplarınızı Azure AD araçlarıyla (Microsoft 365 yönetim merkezi PowerShell gibi) korumanız gerekir. Karma kimlik için, AD DS araçlarıyla şirket içi kullanıcılarınızı ve gruplarınızı koruyabilirsiniz.
- Oturum açma güvenlik gereksinimlerini zorunlu k olmak için kimlik ve cihaz erişimi yapılandırmanızı ekleyin veya değiştirebilirsiniz.

## <a name="next-step"></a>Sonraki adım

[![Adım 4. Şirket içi posta sunucularınızı Office verileri geçirme.](../media/tenant-management-overview/tenant-management-step-grid-migration.png)](tenant-management-migration.md)

Şirket içi [sunucularınızı](tenant-management-migration.md) ve onların verilerini başka Office geçirmek için geçişe Microsoft 365.