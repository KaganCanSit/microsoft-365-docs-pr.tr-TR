---
title: Portala ince grenli erişim vermek için rol tabanlı Microsoft 365 Defender kullanın
description: Portala erişim vermek için güvenlik işlemlerinizin içinde roller ve gruplar oluşturun.
keywords: rbac, rol, tabanlı, erişim, denetim, gruplar, denetim, katman, aad
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
ms.technology: mde
ms.openlocfilehash: 8c1ff743aa6c9c215c3894185a4096c9a35a16e0
ms.sourcegitcommit: 6b24f65c987e5ca06e6d5f4fc10804cdbe68b034
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2021
ms.locfileid: "62996612"
---
# <a name="manage-portal-access-using-role-based-access-control"></a>Rol tabanlı erişim denetimi kullanarak portal erişimini yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Azure Active Directory
- Office 365

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-rbac-abovefoldlink)

Rol tabanlı erişim denetimi (RBAC) kullanarak, portala uygun erişim izni vermek için güvenlik işlemleri ekibi içinde roller ve gruplar oluşturabilirsiniz. Oluşturdukları rollere ve gruplara bağlı olarak, portala erişimi olan kullanıcıların neler göreceği ve neler göreceği üzerinde daha fazla denetime sahip oluruz. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bJ2a]

Coğrafi olarak dağıtılmış büyük güvenlik işlemleri ekipleri normalde güvenlik portallarına erişimi atamak ve yetkilendirmek için katman tabanlı bir model benimser. Normal katmanlar aşağıdaki üç düzeyi içerir:

Katman|Açıklama|
:---|:---|
Katman 1|**Yerel güvenlik işlemleri ekibi / IT ekibi** <br> Bu ekip genellikle coğrafi konum içindeki uyarıları önceler ve araştırır ve etkin bir düzeltmenin gerekli olduğu durumlarda Katman 2'ye ilerler.|
Katman 2|**Bölgesel güvenlik işlemleri ekibi** <br> Bu ekip bölge için tüm cihazları görebilir ve düzeltme eylemleri gerçekleştirebilirsiniz.|
Katman 3|**Global güvenlik işlemleri ekibi** <br> Bu ekip güvenlik uzmanlarından oluşur ve portaldan tüm eylemleri görmeye ve gerçekleştirmeye yetkilidir.|

> [!NOTE]
> Katman 0 varlıkları için, [Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-configure) ve Uç Nokta için Microsoft Defender üzerinde daha ayrıntılı denetim sağlamak için güvenlik yöneticilerine Microsoft 365 Defender.  

Endpoint RBAC için Defender, katman veya rol tabanlı tercih modelinizi destekleyecek şekilde tasarlanmıştır ve hangi rolleri görebilirler, bu roller, erişildeki cihazlar ve gerçekleştir işlemler üzerinde ayrıntılı denetim sağlar. RBAC framework aşağıdaki denetimlerin çevresinde ortalandı:

- **Belirli bir işlemde kimlerin işlemde yer ala bir işlemde olduğunu denetleme**
  - Özel roller oluşturun ve uç nokta özellikleri için Defender'ın ayrıntı bilgilerinden hangilerine erişeyle erişemelerini kontrol altındalar.
- **Belirli cihaz grubu veya gruplarda bilgileri kimlerin göreceğini denetleme**
  - [Adlar,](machine-groups.md) etiketler, etki alanları ve diğerleri gibi belirli ölçütlerle cihaz grupları oluşturun, ardından belirli bir Azure Active Directory (Azure AD) kullanıcı grubunu kullanarak onlara rol erişimi ve iznini verir.

Rol tabanlı erişim uygulamak için yönetici rolleri tanımlamanız, karşılık gelen izinleri atamanız ve rollere atanmış Azure AD kullanıcı grupları atamanız gerekir.

### <a name="before-you-begin"></a>Başlamadan önce

RBAC'yi kullanmadan önce, izin ver gereken rolleri ve RBAC'yi açmanın sonuçlarını anlamanız önemlidir.

> [!WARNING]
> Özelliği etkinleştirmeden önce, Azure AD'de Bir Genel Yönetici rolüne veya Güvenlik Yöneticisi rolüne sahip olmak ve portala kilitlenme riskini azaltmaya hazır Azure AD gruplarınız olması önemlidir. 

Portalda ilk kez oturum Microsoft 365 Defender, size tam erişim veya salt okunur erişim izni ve okunur. Azure AD'de Güvenlik Yöneticisi veya Genel Yönetici rolüne sahip kullanıcılara tam erişim hakları vermektedir. Azure AD'de Güvenlik Okuyucusu rolüne sahip kullanıcılara salt okunur erişim izni verildi. 

Uç Nokta için Defender Genel yönetici rolüne sahip olan birinin, cihaz grubu ilişkilendirmesi ve Azure AD kullanıcı grubu atamalarına bakılmaksızın tüm cihazlara sınırsız erişimi vardır.

> [!WARNING]
> Başlangıçta, yalnızca Azure AD Genel Yöneticisi veya Güvenlik Yöneticisi hakları olan kullanıcılar Microsoft 365 Defender portalında rol oluşturabilir ve atayabilecektir; dolayısıyla, doğru grupların Azure AD'de hazır olması önemlidir.
>
> **Rol tabanlı erişim denetimi açma, salt okunur izinleri olan kullanıcıların (örneğin, Azure AD Güvenlik okuyucu rolüne atanan kullanıcılar) bir role atanana kadar erişimi kaybetmelerine neden olur.** 
>
>Yönetici izinleri olan kullanıcılara otomatik olarak tam izinlere sahip Uç nokta genel yönetici rolü için varsayılan yerleşik Defender atanır. RBAC kullanmayı tercih ettikten sonra, Azure AD Global veya Güvenlik Yöneticileri dışında başka kullanıcıları Uç nokta genel yönetici rolü için Defender'a atabilirsiniz. 
>
> RBAC kullanmayı kabul ettikten sonra, portalda ilk oturum açtığınız gibi ilk rollere geri dönamazsınız.

## <a name="related-topic"></a>İlgili konu

- [RBAC rolleri](../office-365-security/migrate-to-defender-for-office-365-onboard.md#rbac-roles)
- [Uç Nokta için Microsoft Defender'da cihaz grupları oluşturma ve yönetme](machine-groups.md)
