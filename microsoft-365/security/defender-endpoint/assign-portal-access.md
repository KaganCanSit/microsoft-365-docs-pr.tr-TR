---
title: Kullanıcı erişimi ata Microsoft Defender Güvenlik Merkezi
description: Uç nokta için Microsoft Defender portalına okuma ve yazma veya yalnızca okuma erişimi attayabilirsiniz.
keywords: kullanıcı rollerini atama, okuma ve yazma erişimi atama, salt okunur erişim atama, kullanıcı, kullanıcı rolleri, roller
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 11/28/2018
ms.technology: mde
ms.openlocfilehash: fa0157a37cf25efcdcf1b578473b4dc2f6deb10d
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998273"
---
# <a name="assign-user-access-to-microsoft-defender-security-center"></a>Kullanıcı erişimi ata Microsoft Defender Güvenlik Merkezi

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Azure Active Directory
- Office 365
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Uç Nokta için Defender izinleri yönetmek için iki yolu destekler:

- **Temel izin yönetimi**: İzinleri tam erişim veya salt okunur olarak ayarlayın.
- **Rol tabanlı erişim denetimi (RBAC)**: Rolleri tanımlayarak, Azure AD kullanıcı gruplarını rollere ataarak ve kullanıcı gruplarına cihaz gruplarına erişim ataarak ayrıntılı izinleri ayarlayın. RBAC hakkında daha fazla bilgi için bkz [. Rol tabanlı erişim denetimi kullanarak portal erişimini yönetme](rbac.md).

> [!NOTE]
> Zaten temel izinler atadınız, istediğiniz zaman RBAC'ye geçebilirsiniz. Geçiş öncesinde şunları göz önünde yapın:
>
> - Tam erişime sahip kullanıcılara (Azure AD'de Genel Yönetici veya Güvenlik Yöneticisi dizin rolü atanmış olan kullanıcılar), otomatik olarak uç nokta yönetici rolü için varsayılan Defender atanır ve bu rol de tam erişime de sahip olur. RBAC'ye geçiş sonrasında uç nokta için Defender yönetici rolüne ek Azure AD kullanıcı grupları atanabilir. Yalnızca Uç Nokta için Defender yönetici rolüne atanmış kullanıcılar RBAC kullanarak izinleri yönetebilir. 
> - Salt okunur erişimi olan (Güvenlik Okuyucuları) kullanıcılar, kendilerine rol atanana kadar portala erişimi kaybeder. RBAC altında yalnızca Azure AD kullanıcı gruplarına rol atanabilir.
> - RBAC'ye geçiş sonrasında, temel izin yönetimini kullanmaya geri dönmezsiniz.

## <a name="related-topics"></a>İlgili konular

- [Portala erişmek için temel izinleri kullanma](basic-permissions.md)
- [RBAC kullanarak portal erişimini yönetme](rbac.md)
