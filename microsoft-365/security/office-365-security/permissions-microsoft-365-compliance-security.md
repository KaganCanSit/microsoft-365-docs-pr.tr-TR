---
title: Güvenlik merkezi Microsoft 365 uyumluluk merkezi izinler
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
ms.audience: Admin
ms.topic: article
audience: Admin
localization_priority: Priority
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Güvenlik merkezi veya Microsoft 365 kullanarak, Microsoft 365 uyumluluk merkezi veya uyumlulukla ilgili tüm görevler için izinleri merkezi olarak yönetebilirsiniz.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: cc2808ffe5d0acd3a5c3c3a6252503ee5e2cf94e
ms.sourcegitcommit: e8f5d88f0fe54620308d3bec05263568f9da2931
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2021
ms.locfileid: "62959640"
---
# <a name="permissions-in-the-microsoft-365-compliance-center-and-microsoft-365-security-center"></a>Güvenlik merkezi Microsoft 365 uyumluluk merkezi Microsoft 365 izinler

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Tüm standart hizmetlerde yer alan uyumluluk ve güvenlik senaryolarını Microsoft 365 gerekir. Ayrıca, kurum un IT grubunda doğru kullanıcılara doğru yönetici izinlerini verme esnekliğine de ihtiyacınız vardır. Güvenlik merkezi veya Microsoft 365 kullanarak, Microsoft 365 uyumluluk merkezi veya uyumlulukla ilgili tüm görevler için izinleri merkezi olarak yönetebilirsiniz.

Genel yönetici kullanıcıları bu yönetici rollerine ekledikten sonra, bu yönetici Microsoft 365'daki Microsoft 365 güvenlik merkezi, Microsoft 365 uyumluluk merkezi, Azure ve Office 365 gibi tüm hizmetlere yayılan özelliklere ve verilere erişim iznine sahip olur Enterprise Mobility + Security.

## <a name="what-the-microsoft-365-roles-are"></a>Rollerin Microsoft 365 nedir?

Güvenlik merkezi'nde Microsoft 365 uyumluluk merkezi Microsoft 365 roller Azure Active Directory. Bu roller, bir kişiye işini yapmak için gereken tüm izinleri vermenizi kolaylaştıran, kuruluşun IT grubunda bulunan iş işlevleriyle uyumlu olacak şekilde tasarlanmıştır.

****

|Rol|Açıklama|
|---|---|
|**Genel yönetici**|Tüm hizmetlerde, tüm yönetim Microsoft 365 erişim. Yalnızca genel yöneticiler diğer yönetici rollerini atayır. Daha fazla bilgi için bkz [. Genel Yönetici / Şirket Yöneticisi](/azure/active-directory/roles/permissions-reference#global-administrator--company-administrator).|
|**Uyumluluk veri yöneticisi**|Tüm dünya genelinde verilerinizi takip edin, Microsoft 365 korunmasına yardımcı olun ve riskleri azaltmak için tüm sorunlar hakkında içgörüler elde edin. Daha fazla bilgi için bkz. [Uyumluluk Veri Yöneticisi](/azure/active-directory/roles/permissions-reference#compliance-data-administrator).|
|**Uyumluluk yöneticisi**|Tüm yasal düzenleme gereksinimleriyle uyumlu kalmalarına, eBulma olaylarını yönetmelerine ve farklı konumlarda Microsoft 365, kimliklerde ve uygulamalarda veri yönetimi ilkelerini korumalarına yardımcı olun. Daha fazla bilgi için bkz. [Uyumluluk Yöneticisi](/azure/active-directory/roles/permissions-reference#compliance-administrator).|
|**Güvenlik operatörü**|Kullanıcılarınızı, cihazlarınızı ve içeriğinizi görüntüleme, araştırma ve Microsoft 365 tehditlere yanıt verme. Daha fazla bilgi için bkz. [Güvenlik İşleci](/azure/active-directory/roles/permissions-reference#security-operator).|
|**Güvenlik gözetmeni**|Kullanıcılarınıza, cihazlarınıza ve Microsoft 365 yönelik etkin tehditleri  görüntüleme ve araştırmanız gerekir, ancak (Güvenlik işlecinin aksine) herhangi bir işlem gerçekleştirerek bu izinleri olmaz. Daha fazla bilgi için bkz. [Güvenlik Okuyucu](/azure/active-directory/roles/permissions-reference#security-reader).|
|**Güvenlik yöneticisi**|Güvenlik ilkelerini yöneterek, Microsoft 365 ürünleri genelinde güvenlik analizlerini ve raporlarını gözden geçirerek ve tehdit ortamında hızlendirerek, kuruluşun genel güvenliğini kontrol edin. Daha fazla bilgi için bkz. [Güvenlik Yöneticisi](/azure/active-directory/roles/permissions-reference#security-administrator).|
|**Genel okuyucu**|Genel yönetici rolünün salt **okunur sürümü** . Tüm ayarları ve yönetim bilgilerini tüm Microsoft 365. Daha fazla bilgi için bkz. [Genel Okuyucu](/azure/active-directory/roles/permissions-reference#global-reader).|
|

## <a name="global-administrators-can-manage-roles-in-azure-active-directory"></a>Genel yöneticiler iş yerlerinde rolleri Azure Active Directory

Microsoft 365 uyumluluk merkezi ve Microsoft 365 merkezinde, bir rol seçerek, bu rolün atamalarını görüntüabilirsiniz. Ancak bu ödevleri yönetmek için diğer Azure Active Directory.

Daha fazla bilgi için bkz[. 2010'da yönetici rollerini görüntüleme Azure Active Directory](/azure/active-directory/users-groups-roles/directory-manage-roles-portal).

![E-postada izinleri yönetme Azure Active Directory](../../media/permissions-manage-in-azure-ad-link.png)

## <a name="managing-roles-in-a-service-instead-of-azure-active-directory"></a>Rol yönetimi yerine hizmette Azure Active Directory

Güvenlik merkezinde ve Microsoft 365 uyumluluk merkezi Microsoft 365 rolleri, izinleri olan hizmetlerde de görünür. Örneğin, bu rolleri Güvenlik ve Uyumluluk Merkezi'& göresiniz.

![Güvenlik ve Uyumluluk &'daki roller](../../media/m365-roles-in-o365-scc.png)

Bu rollerin Güvenlik ve Uyumluluk Merkezi'nde & için bkz. Güvenlik ve Uyumluluk [Merkezi'&.](permissions-in-the-security-and-compliance-center.md)

### <a name="breaking-inheritance"></a>Devralmayı kes

Bu rolleri iş yerlerinde yönetirken, bu Azure Active Directory tüm iş hizmetleri için merkezi olarak Microsoft 365 önemlidir. Bununla birlikte, Güvenlik ve Uyumluluk Merkezi gibi belirli bir hizmette rol &, rolü yalnızca o hizmet **için** yönetirsiniz. Bir hizmette rol için yapılan atamalar ve izinler, rol için verilen tüm izinleri Azure Active Directory geçersiz kılar.

Bu yararlı olabilir. Örneğin, Güvenlik yöneticisi rolüne atanan bir kişinin olayları yönetme izinleri yok. Ancak, uç nokta için Microsoft Defender'da bu izinleri kullanarak, o hizmette olay yönetimine özel izinler veebilirsiniz.

## <a name="where-to-find-role-information-for-each-microsoft-365-service"></a>Her hizmet için rol bilgileri Microsoft 365 bulma

Kullanıcıya uyumluluk veya güvenlik yöneticisi rollerinden Microsoft 365 atadığınız için, o kullanıcıya çeşitli kullanıcı hizmetleri için Microsoft 365 atarsınız. Her hizmette bir rolle ilgili belirli izinler hakkında daha fazla bilgi bulmak için aşağıdaki bağlantıları kullanın.

****

|Microsoft 365 hizmeti|Rol bilgileri|
|---|---|
|İşletmeler için Office 365 Microsoft 365 planlarında yönetici rolleri|[Microsoft 365 rollerini seçin](../../admin/add-users/about-admin-roles.md)|
|Azure Active Directory (Azure AD) ve Azure AD Identity Protection|[Azure AD yönetici rolleri](/azure/active-directory/users-groups-roles/directory-assign-admin-roles)|
|Kimlik için Microsoft Defender|[Kimlik rol grupları için Microsoft Defender](/azure-advanced-threat-protection/atp-role-groups)|
|Azure Information Protection|[Azure AD yönetici rolleri](/azure/active-directory/users-groups-roles/directory-assign-admin-roles)|
|Uyumluluk Yöneticisi|[Uyumluluk Yöneticisi](../../compliance/compliance-manager-setup.md#set-user-permissions-and-assign-roles)|
|Exchange Online|[Exchange tabanlı erişim denetimi](/exchange/permissions-exo/permissions-exo)|
|Intune|[Intune rol tabanlı erişim denetimi](/intune/role-based-access-control)|
|Yönetilen Masaüstü|[Azure AD yönetici rolleri](/azure/active-directory/users-groups-roles/directory-assign-admin-roles)|
|Microsoft Cloud App Security|[Rol tabanlı erişim denetimi](/cloud-app-security/manage-admins)|
|Güvenlik & Uyumluluk Merkezi|[Microsoft 365 rollerini seçin](permissions-in-the-security-and-compliance-center.md)|
|Privileged Identity Management|[Azure AD yönetici rolleri](/azure/active-directory/users-groups-roles/directory-assign-admin-roles)|
|Güvenli Puan|[Azure AD yönetici rolleri](/azure/active-directory/users-groups-roles/directory-assign-admin-roles)|
|SharePoint Online|[Azure AD yönetici rolleri](/azure/active-directory/users-groups-roles/directory-assign-admin-roles) <p> [SharePoint Online yönetici rolü hakkında](/sharepoint/sharepoint-admin-role)|
|Teams/Skype Kurumsal|[Azure AD yönetici rolleri](/azure/active-directory/users-groups-roles/directory-assign-admin-roles)|
|Uç Nokta için Microsoft Defender|[Uç nokta rol tabanlı erişim denetimi için Microsoft Defender](/windows/security/threat-protection/windows-defender-atp/rbac-windows-defender-advanced-threat-protection)|
|

## <a name="coming-soon"></a>Çok yakında

Güvenlik merkezinde ve güvenlik merkezinde izinler Microsoft 365 uyumluluk merkezi Microsoft 365 üzerinde çalışıyoruz. Örneğin, şu anda şunları yapma özelliği için destek üzerinde çalışıyoruz:

- Rollarınızı güvenlik Microsoft 365 uyumluluk merkezi Microsoft 365 yerine güvenlik merkezinden Azure Active Directory.
- Belirli izinler ekleyerek veya kaldırarak rolleri özelleştirin.
- Seçtiğiniz izinlerle özel roller oluşturun.