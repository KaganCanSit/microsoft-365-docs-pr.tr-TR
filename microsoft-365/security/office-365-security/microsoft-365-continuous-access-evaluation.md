---
title: Kuruluş için sürekli erişim Microsoft 365 - Microsoft 365 değerlendirme
description: Microsoft 365 Azure AD ve Azure AD için koşullu erişim değerlendirmenin etkin kullanıcı oturumlarını nasıl önceden sonlandırıyor ve yakın zamanda kiracı ilkesi değişikliklerini nasıl zorunlu olduğunu açıklar.
ms.author: josephd
author: JoeDavies-MSFT
manager: dansimp
ms.prod: m365-security
ms.topic: article
audience: Admin
f1.keywords:
- NOCSH
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- m365solution-identitydevice
- m365solution-scenario
ms.technology: mdo
ms.openlocfilehash: 376b15a6faa84b26ab7e48356e54c0456da16072
ms.sourcegitcommit: aac7e002ec6e10a41baa2d0bd38614b0ed471a70
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63009999"
---
# <a name="continuous-access-evaluation-for-microsoft-365"></a>Web için sürekli erişim Microsoft 365

Geleneksel kimlik doğrulaması için OAuth 2.0 kullanan modern bulut hizmetleri, kullanıcı hesabının erişimini iptal etmek için erişim belirtecinin süresinin dolmasını kullanır. Uygulamada, bu durum yöneticinin kullanıcı hesabının erişimini iptal etmese bile, ilk iptal etkinliği gerçekleştikten sonra varsayılan olarak Microsoft 365 için bir saate kadar olan erişim belirteci süresi dolana kadar kullanıcının erişimi olduğu anlamına gelir.

Microsoft 365 Azure Active Directory (Azure AD) için koşullu erişim değerlendirmesi, erişim belirteci süresinin dolmasına güvenmek yerine etkin kullanıcı oturumlarını önceden sonlandırılır ve kiracı ilkesi değişikliklerini gerçek zamanlı olarak zorlar. Kullanıcı hesabı veya kiracı, kullanıcı hesabının kimlik doğrulama durumunun yeniden değerlendirilmesini gerektiren şekilde değiştirildiğinde, Azure AD sürekli erişim değerlendirme özelliği etkin Microsoft 365 hizmetlerini (SharePoint, Teams ve Exchange gibi) onaylatır.

Outlook gibi sürekli erişim değerlendirme özelliği etkinleştirilmiş bir istemci var olan bir erişim belirteciyle Exchange erişmeye çalıştığında, belirteç hizmet tarafından reddedilir ve yeni bir Azure AD kimlik doğrulaması istenir. Sonuç, kullanıcı hesabı ve ilke değişikliklerinin neredeyse gerçek zamanlı zorlaması olur.

bazı ek avantajlardan bazıları:

- Azure AD IP adresi konum ilkesi aracılığıyla, kuruluş dışında geçerli bir erişim belirteci kopyaları ve dışarı aktaran kötü niyetli Insider'lar için, sürekli erişim değerlendirme bu belirtecin kullanımını engellemez. Sürekli erişim değerlendirmeyle, Azure AD ilkeleri desteklenen Microsoft 365 hizmetleriyle eşitler, böylece bir erişim belirteci ilkenin IP adresi aralığının dışından hizmete erişmeye çalışırsa, hizmet belirteci reddeder.

- Sürekli erişimin değerlendirilmesi, daha az belirteç yenilemesi gerektirerek daha yüksek performansı sağlar. Destek hizmetleri yeniden kimlik doğrulaması gerektirmeyle ilgili önceden bildirim alsa da, Azure AD bir saatten daha uzun süre önce, daha uzun yaşayan belirteçler verilmesine neden olabilir. Daha uzun yaşanacak belirteçlerle, istemcilerin Azure AD'den o kadar sık belirteç yenilemesi talep etmek zorunda kalmaları gerekmeyecektir, bu nedenle kullanıcı deneyimi daha dayancı olur.

Aşağıda, sürekli erişim değerlendirmesinde kullanıcı erişim denetimi güvenliğini artıran durumlara bazı örnekler verilmiştir:

- Bir yöneticinin mevcut tüm oturumları geçersiz kılınarak parolasını kullanıcı hesabının parolası geçersiz olduğu için kullanıcı Microsoft 365 yönetim merkezi. Gerçek zamanlı olarak mevcut tüm kullanıcı oturumları Microsoft 365 geçersiz kılındı.

- Word'de bir belge üzerinde çalışan bir kullanıcı tabletini yönetici tarafından tanımlanan ve onaylanmış IP adresi aralığında olmayan bir açık kahveciye alır. Kafede, kullanıcının belgeye erişimi hemen engellenir.

Örneğin Microsoft 365 sürekli erişim değerlendirme şu anda şunları destekler:

- Exchange, SharePoint hizmetleri Teams.
- Outlook tarayıcısında Outlook, Teams, Office ve OneDrive tarayıcılarında ve Win32, iOS, Android ve Mac istemcileri için kullanılabilir.

Microsoft, sürekli erişim değerlendirmesini Microsoft 365 hizmet ve istemci desteği sağlamak için ek hizmetler ve istemciler üzerinde çalışıyor.

Sürekli erişim değerlendirme, tüm çalışma sürümlerine, çalışma Office 365 Microsoft 365. Koşullu Erişim ilkelerini yapılandırmak için, Azure AD Premium P1 sürümlerin tamamlarına dahil olan Microsoft 365 gerekir.

> [!NOTE]
> Sürekli [erişim değerlendirme](/azure/active-directory/conditional-access/concept-continuous-access-evaluation#limitations) sınırlamaları için bu makaleye bakın.

## <a name="scenarios-supported-by-microsoft-365"></a>Microsoft 365 tarafından desteklenen senaryolar

Sürekli erişim değerlendirme iki tür etkinlik destekler:

- Kritik olaylar, kullanıcının erişimini kaybetmesi gereken olaylardır.
- Koşullu Erişim ilkesi değerlendirme, kullanıcının yönetici tanımlı bir ilkeye dayalı olarak kaynağa erişimini kaybetmesi gerektiği zaman oluşur.

Kritik olaylar şunlardır:

- Kullanıcı hesabı devre dışı
- Parola değişti
- Kullanıcı oturumları iptal edildi
- Multifactor authentication is enabled for the user
- Azure AD Kimlik Koruması'nın erişiminin değerlendirilmesina bağlı olarak [artırılmış hesap riski](/azure/active-directory/identity-protection/overview-identity-protection)

Koşullu Erişim ilkesi değerlendirme, kullanıcı hesabı artık güvenilir bir ağdan bağlanmazsa gerçekleşir.

Aşağıdaki örnek Microsoft 365 hizmetleri şu anda Azure AD'den gelen olayları dinleyerek sürekli erişim değerlendirmesini destekler.

<br>

****

|Zorlama türü|Exchange|SharePoint|Teams|
|---|---|---|---|
|**Kritik olaylar:**||||
|Kullanıcı iptali|Destekleniyor|Destekleniyor|Destekleniyor|
|Kullanıcı riski|Destekleniyor|Desteklenmiyor|Desteklenmiyor|
|**Koşullu Erişim ilkesi değerlendirme:**||||
|IP adresi konum ilkesi|Destekleniyor|Destekleniyor\*|Destekleniyor|
|

\*SharePoint Office tarayıcı erişimi katı modu etkinleştirerek anında IP ilkesi zorlamasını destekler. Kesin mod olmadan, erişim belirtecinin yaşam süresi bir saat olur.

Koşullu Erişim ilkesi ayarlama hakkında daha fazla bilgi için bu [makaleye bakın](/azure/active-directory/conditional-access/overview).

## <a name="microsoft-365-clients-supporting-continuous-access-evaluation"></a>Microsoft 365 erişim değerlendirmesini destekleyen en iyi istemciler

Microsoft 365 için sürekli erişim değerlendirme özelliği etkinleştirilmiş istemciler, bir kullanıcı oturumunun yeniden kimlik doğrulaması için Azure AD'ye yeniden yönlendirmesi olan, önbelleğe alınmış bir kullanıcı belirteci sürekli erişim değerlendirme özelliği etkin bir kullanıcı hizmeti tarafından reddedildiğinde bir talep Microsoft 365 destekler.

Aşağıdaki istemciler web, Win32, iOS, Android ve Mac üzerinde sürekli erişim değerlendirmesini destekler:

- Outlook
- Teams
- Office\*
- SharePoint
- OneDrive

\*Görev iddia edin, web için Office desteklenmiyor.

Sürekli erişim değerlendirmesini desteklemez istemciler için erişim belirtecinin yaşam Microsoft 365 bir saat varsayılan olarak kalır.

## <a name="see-also"></a>Ayrıca bkz.

- [Sürekli erişim değerlendirme](/azure/active-directory/conditional-access/concept-continuous-access-evaluation)
- [Koşullu Erişim belgeleri](/azure/active-directory/conditional-access/overview)
- [Azure AD Kimlik Koruması belgeleri](/azure/active-directory/identity-protection/overview-identity-protection)
