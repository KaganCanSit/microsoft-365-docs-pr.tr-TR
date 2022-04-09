---
title: Rol tabanlı erişim denetimi için özel roller
description: Microsoft 365 Defender portalında özel rolleri yönetmeyi öğrenin
keywords: erişim, izinler, Microsoft 365 Defender, M365, güvenlik, MCAS, Bulut Uygulamaları Güvenliği, Uç Nokta için Microsoft Defender , kapsam, kapsam, RBAC, rol tabanlı erişim, özel rol tabanlı erişim, roller tabanlı kimlik doğrulaması, MDO'da RBAC, roller, rol grupları, izin devralma, ayrıntılı izinler
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 94330e319eeb44618c1e11b27da7b3d63c08d203
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2021
ms.locfileid: "64731361"
---
# <a name="custom-roles-in-role-based-access-control-for-microsoft-365-defender"></a>Microsoft 365 Defender için rol tabanlı erişim denetiminde özel roller

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

[!INCLUDE [Prerelease](../includes/prerelease.md)]

**Şunlar için geçerlidir:**

- Microsoft 365 Defender
 
Microsoft 365 Defender erişmek için kullanılabilecek iki tür rol vardır:
- **Genel Azure Active Directory (AD) rolleri**
- **Özel roller**

Microsoft 365 Defender erişimi, [Azure Active Directory genel rolleri kullanılarak toplu olarak yönetilebilir (AAD)](m365d-permissions.md)

Daha fazla esnekliğe ve belirli ürün verilerine erişim üzerinde denetime ihtiyacınız varsa, Microsoft 365 Defender erişim ilgili her güvenlik portalı aracılığıyla Özel roller oluşturularak da yönetilebilir.  

Örneğin, Uç Nokta için Microsoft Defender aracılığıyla oluşturulan özel bir rol, Microsoft 365 Defender portalındaki Uç nokta verileri de dahil olmak üzere ilgili ürün verilerine erişime izin verebilir. Benzer şekilde, Office 365 için Microsoft Defender aracılığıyla oluşturulan bir Özel rol, Microsoft 365 Defender portalındaki E-posta & işbirliği verileri de dahil olmak üzere ilgili ürün verilerine erişime izin verir.

Mevcut Özel rollere sahip kullanıcılar, ek yapılandırma gerekmeyen mevcut iş yükü izinlerine göre Microsoft 365 Defender portalındaki verilere erişebilir.

## <a name="create-and-manage-custom-roles"></a>Özel roller oluşturma ve yönetme
Aşağıdaki güvenlik portallarının her biri aracılığıyla özel roller ve izinler oluşturulabilir ve tek tek yönetilebilir: 

- Uç Nokta için Microsoft Defender – [Uç Nokta için Microsoft Defender'da rolleri düzenleme](../defender-endpoint/user-roles.md)
- Office 365 için Microsoft Defender – [Güvenlik & Uyumluluk Merkezi'ndeki İzinler](../office-365-security/permissions-in-the-security-and-compliance-center.md?preserve-view=true&view=o365-worldwide)
- Microsoft Defender for Cloud Apps – [Yönetici erişimini yönetme](/cloud-app-security/manage-admins)

Tek bir portal aracılığıyla oluşturulan her özel rol, ilgili ürün portalının verilerine erişim sağlar. Örneğin, Uç Nokta için Microsoft Defender aracılığıyla oluşturulan özel bir rol yalnızca Uç Nokta için Defender verilerine erişime izin verir.

> [!TIP]
> İzinlere ve rollere gezinti bölmesinden İzinler & rolleri seçilerek Microsoft 365 Defender portalı üzerinden de erişilebilir. Microsoft Defender for Cloud Apps erişimi, Bulut için Defender Uygulamaları portalı üzerinden yönetilir ve Kimlik için Microsoft Defender erişimi de denetler.  [Bkz. Microsoft Defender for Cloud Apps](/cloud-app-security/manage-admins)

> [!NOTE]
> Microsoft Defender for Cloud Apps'de oluşturulan özel rollerin de Kimlik için Microsoft Defender verilere erişimi vardır. Kullanıcı grubu yöneticisi veya Uygulama/örnek yöneticisi Microsoft Defender for Cloud Apps rolleri olan kullanıcılar Microsoft 365 Defender portalı üzerinden Microsoft Defender for Cloud Apps verilere erişemez.

## <a name="manage-permissions-and-roles-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında izinleri ve rolleri yönetme
İzinler ve roller Microsoft 365 Defender portalında da yönetilebilir:

1. security.microsoft.com Microsoft 365 Defender portalında oturum açın.
2. Gezinti bölmesinde **İzinler & roller'i** seçin.
3. **İzinler** üst bilgisinin altında **Roller'i** seçin.

> [!NOTE]
> Bu yalnızca Office 365 için Defender ve Uç Nokta için Defender için geçerlidir. Diğer iş yükleri için erişim ilgili portallarında yapılmalıdır.


## <a name="required-roles-and-permissions"></a>Gerekli roller ve izinler
Aşağıdaki tabloda, her iş yükündeki her bir birleşik deneyime erişmek için gereken roller ve izinler özetlenmiştir. Aşağıdaki tabloda tanımlanan roller, tek tek portallardaki özel rollere başvurur ve benzer şekilde adlandırılmış olsa bile Azure AD'deki genel rollere bağlı değildir.

> [!NOTE]
> Olay yönetimi, olayın parçası olan tüm ürünler için yönetim izinleri gerektirir.
 
| **Microsoft 365 Defender için aşağıdaki rollerden biri gereklidir**  | **Uç Nokta için Defender için aşağıdaki rollerden biri gereklidir**  | **Office 365 için Defender için aşağıdaki rollerden biri gereklidir** | **Bulut için Defender Uygulamaları için aşağıdaki rollerden biri gereklidir** | 
|---------|---------|---------|---------|
| Araştırma verilerini görüntüleme: <ul><li>Uyarı sayfası</li> <li>Uyarı sırası</li> <li>Olaylar</li>  <li>Olay kuyruğu</li> <li>İşlem merkezi</li></ul>| Veri görüntüleme- güvenlik işlemleri | <ul><li>Yalnızca görüntüleme Uyarılarını yönetme </li> <li>Kuruluş yapılandırması</li><li>Denetim günlükleri</li> <li>Yalnızca görüntüleme denetim günlükleri</li> <li>Güvenlik gözetmeni</li> <li>Güvenlik yöneticisi</li><li>Yalnızca görüntüleme alıcıları</li></ul>  | <ul><li>Genel yönetici</li> <li>Güvenlik yöneticisi</li> <li>Uyumluluk yöneticisi</li> <li>Güvenlik operatörü</li> <li>Güvenlik gözetmeni</li> <li>Genel gözetmen</li></ul> |
| Tehdit avcılığı verilerini görüntüleme | Veri görüntüleme- güvenlik işlemleri | <ul><li>Güvenlik gözetmeni</li> <li>Güvenlik yöneticisi</li> <li>Yalnızca görüntüleme alıcıları</li> | <ul><li>Genel yönetici</li> <li>Güvenlik yöneticisi</li> <li>Uyumluluk yöneticisi</li> <li>Güvenlik operatörü</li> <li>Güvenlik gözetmeni</li> <li>Genel gözetmen</li></ul> |
| Uyarıları ve olayları yönetme | Uyarı araştırması | <ul><li>Uyarıları yönetin</li> <li>Güvenlik yöneticisi</li> | <ul><li>Genel yönetici</li> <li>Güvenlik yöneticisi</li> <li>Uyumluluk yöneticisi</li> <li>Güvenlik operatörü</li> <li>Güvenlik gözetmeni</li></ul> |
| İşlem merkezi düzeltmesi | Etkin düzeltme eylemleri – güvenlik işlemleri | Arama ve temizleme | |
| Özel algılamaları ayarlama | Güvenlik ayarlarını yönetme |<ul><li>Uyarıları yönetin</li> <li>Güvenlik yöneticisi</li></ul> | <ul><li>Genel yönetici</li> <li>Güvenlik yöneticisi</li> <li>Uyumluluk yöneticisi</li> <li>Güvenlik operatörü</li> <li>Güvenlik gözetmeni</li> <li>Genel gözetmen</li></ul> |
| Tehdit Analizi | Uyarılar ve olay verileri: <ul><li>Veri görüntüleme- güvenlik işlemleri</li></ul>TVM risk azaltmaları:<ul><li>Verileri görüntüleme - Tehdit ve güvenlik açığı yönetimi</li></ul> | Uyarılar ve olay verileri:<ul> <li>Yalnızca görüntüleme Uyarılarını yönetme</li> <li>Uyarıları yönetin</li> <li>Kuruluş yapılandırması</li><li>Denetim günlükleri</li> <li>Yalnızca görüntüleme denetim günlükleri</li><li>Güvenlik gözetmeni</li> <li>Güvenlik yöneticisi</li><li>Yalnızca görüntüleme alıcıları</li> </ul> Engellenen e-posta girişimleri: <ul><li>Güvenlik gözetmeni</li> <li>Güvenlik yöneticisi</li><li>Yalnızca görüntüleme alıcıları</li> | Bulut için Defender Uygulamaları veya MDI kullanıcıları için kullanılamaz |

Örneğin, Uç Nokta için Microsoft Defender gelen tehdit avcılığı verilerini görüntülemek için Veri güvenliği işlemlerini görüntüleme izinleri gereklidir.  

Benzer şekilde, Office 365 için Microsoft Defender avlanma verilerini görüntülemek için kullanıcılar aşağıdaki rollerden birine ihtiyaç duyar:  

- Veri güvenliği işlemlerini görüntüleme
- Güvenlik gözetmeni
- Güvenlik yöneticisi
- Yalnızca görüntüleme alıcıları

## <a name="related-topics"></a>İlgili konular
- [RBAC rolleri](../office-365-security/migrate-to-defender-for-office-365-onboard.md#rbac-roles)
- [Microsoft 365 Defender erişimini yönetme](m365d-permissions.md)
- [Bulut için Defender Uygulamaları için yönetici erişimini yönetme](/cloud-app-security/manage-admins)
