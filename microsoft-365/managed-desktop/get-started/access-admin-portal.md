---
title: Yönetici portalına erişme
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
description: Yönetici portalını bulma ve kullanma; erişimi denetleme gibi.
ms.service: m365-md
ms.author: tiaraquan
author: tiaraquan
ms.topic: article
audience: ITPro
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.openlocfilehash: 89170c4479af29e9a4b3f46fa3b44ae2fcfa5500
ms.sourcegitcommit: d4797cfc15c732f1a7ef21e4f944e672a7170f9a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2022
ms.locfileid: "62973882"
---
# <a name="access-the-admin-portal"></a>Yönetici portalına erişme

Microsoft Yönetilen Masaüstü hizmetine ağ geçidiniz [Microsoft Endpoint Manager](https://endpoint.microsoft.com/). Cihaz yönetimi için bu portalın özelliklerini biliyorsanız, aşağıdaki Microsoft Endpoint Manager [bakın](/mem/).

> [!NOTE]
> [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) tarayıcılar desteklenir:
> - Microsoft Edge (en son sürüm)
> - Safari (yalnızca en son sürüm, Mac)
> - Chrome (en son sürüm)
> - Firefox (en son sürüm)

Microsoft Yönetilen Masaüstü yönetim özelliklerine erişmek için, yönetim hesabınız için belirli izinler Microsoft Endpoint Manager.

Rol tabanlı erişim denetimi kullanarak, kuruluş içinde bu özelliklere yönetici erişimini yönetsiniz. Microsoft Azure Active Directory Yönetim portalı içinde farklı özelliklere daha ayrıntılı denetim sağlamak için çeşitli yönetici rolleri (Azure AD) ve yerleşik Microsoft Yönetilen Masaüstü rolleri kullanılabilir. Bu roller hakkında daha Azure Active Directory için bkz. [Azure AD yerleşik rolleri](/azure/active-directory/roles/permissions-reference).

Çeşitli Microsoft ürünleri ve hizmetleri için geçerli olan Azure AD yönetici rollerinden farklı olarak, yerleşik roller Microsoft Yönetilen Masaüstü'ne özeldir ve yalnızca bu hizmetin Yönetici özelliklerine erişimi garanti altına alır. Yöneticiler, var olan yönetici hesaplarına Microsoft Yönetilen Masaüstü izinlerini eklemek için kullanıcılara tek tek veya Azure AD yönetici rolleri ile birlikte yerleşik roller atayabilirsiniz.

## <a name="azure-active-directory-roles-with-microsoft-managed-desktop-access"></a>Azure Active Directory Yönetilen Masaüstü erişimiyle daha fazla rol

| Azure AD rolü | Microsoft Yönetilen Masaüstü izinleri |
| ----- | ----- |
| Genel Yönetici | Bu role sahip yöneticiler, Microsoft Yönetilen **Masaüstü Yöneticisi portalında yer alan tüm** özellikler için okuma ve yazma izinlerine sahip olur. |
| Genel Okuyucu | Bu role sahip yöneticiler Microsoft Yönetilen **Masaüstü Yöneticisi portalında yer alan** tüm özellikler için salt okunur izinlere sahip olur. |
| Intune Hizmet Yöneticisi | Bu role sahip yöneticiler, Microsoft **Yönetilen Masaüstü Yöneticisi portalında** güvenlikle ilgili değil, okuma ve yazma izinlerine sahip olur. |
| Hizmet Destek Yöneticisi | Bu role sahip yöneticiler, Microsoft Yönetilen  Masaüstü Yöneticisi portalında yükseltme istekleri dahil olmak üzere destek isteklerini  yönetmek için güvenlik ve yazma izinleriyle ilgili olmayan özellikler üzerinde salt okunur izinlere sahip olur. |
| Güvenlik Yöneticisi | Bu role sahip yöneticiler, Yönetim **portalında** yer alan Microsoft Yönetilen Masaüstü'ne ilişkin güvenlikle ilgili özellikler için tüm özellikler **üzerinde** salt okunur izinlere ve yazma izinlerine sahip olur. |
| Güvenlik Okuyucu |Bu role sahip yöneticiler Microsoft Yönetilen **Masaüstü Yöneticisi portalında yer alan** tüm özellikler için salt okunur izinlere sahip olur. |

Yönetici rollerini atamayla ilgili Azure Active Directory için [bkz. Azure AD yerleşik rolleri](/azure/active-directory/roles/permissions-reference).

> [!IMPORTANT]
> Yalnızca Genel Yönetici rolünün, kurumlarınızı Microsoft Yönetilen *Masaüstü'ne* kaydetmek için gerekli izinleri vardır. Farklı rollere Azure Active Directory, kullanıcı hesaplarına çeşitli kullanıcılar için ayrıcalıklar ve Microsoft hizmetleri. Microsoft Yönetilen Masaüstü ile kaydı tamamladıktan sonra, bu rolü her zaman diğer görevlerinizi tamamlamak için *gereken* en az ayrıcalıkla kullan olmanız gerekir.

## <a name="built-in-roles-provided-by-microsoft-managed-desktop"></a>Microsoft Yönetilen Masaüstü tarafından sağlanan yerleşik roller

Aşağıda Microsoft Yönetilen Masaüstü tarafından sağlanan yerleşik roller verilmektedir:

| Yerleşik rol | Microsoft Yönetilen Masaüstü izinleri |
| ----- | ----- |
| Microsoft Yönetilen Masaüstü Hizmeti Yöneticisi | Bir kullanıcıya atandığı zaman, bu rol yöneticiye Microsoft Yönetilen Masaüstü Yönetimi portalında güvenlikle ilgili olarak yer alan **Microsoft** Yönetilen Masaüstü özellikleri için okuma ve yazma izinleri verir. |
| Microsoft Yönetilen Masaüstü Hizmeti Okuyucusu | Bir kullanıcıya atandığı zaman, bu rol yöneticiye Microsoft Yönetilen Masaüstü Yöneticisi portalında güvenlikle ilgili olmayan **, salt okunur Microsoft** Yönetilen Masaüstü özellikleri üzerinde izinler verir. |
| Microsoft Yönetilen Masaüstü Güvenlik Yöneticisi | Bir kullanıcıya atandığı zaman, bu rol o yöneticiye  yalnızca Microsoft Yönetilen Masaüstü Yöneticisi portalında güvenlikle ilgili özellikler için okuma ve yazma izinleri verir. |
| Microsoft Yönetilen Masaüstü Desteği İş Ortağı |Bir kullanıcıya atandığı zaman, bu rol yöneticiye yalnızca  yükseltme istekleri oluşturma ve yönetme, ayrıca Microsoft Yönetilen Masaüstü Yöneticisi portalında iş ortağına yönlendirme istekleri oluşturma ve yönetme izinleri verir. |

> [!NOTE]
> Güvenlik özellikleri arasında güvenlikle ilgili iletişimler, güvenlik ilgili kişilerinin yönetimi, güvenlikle ilgili destek isteklerinin yönetimi ve güvenlikle ilgili raporlara erişim yer almaktadır.

### <a name="assigning-built-in-roles-to-user"></a>Kullanıcıya yerleşik roller atama

Yerleşik rollerin kolay yönetimi için, her özel rol için "Modern Çalışma Alanı Rolleri - Rol Adı" adı bulunan bir _güvenlik grubu_ vardır. Örneğin, "Modern Çalışma Alanı Rolleri – Güvenlik Yöneticisi").

**Kullanıcıları şu güvenlik gruplarından birini atamak için:**

1. Portala Microsoft Endpoint Manager gidin.
2. Sol bölmede Gruplar'ı **seçin**.
3. Modern **Çalışma Alanı Rollerini** arayın ve atamak istediğiniz rolle ilişkilendirilmiş grubu seçin.
4. Sol **tarafta** Üyeler'i seçin ve ardından komut çubuğunda **+ Üye** ekle'yi seçin.
5. Eklenen kişinin e-posta adresini girin. Konuksa, grubu atamadan önce bu kişileri davet etmelisiniz.
6. **Alttaki** Seç'i seçin.

> [!NOTE]
> Rol ataması için güvenlik gruplarını iç içe yerleştirme şu anda desteklenmiyor.

### <a name="assigning-built-in-roles-to-groups"></a>Gruplara yerleşik roller atama

**Var olan bir gruba yerleşik rollerden birini veya birden fazlasını atamak için:**

1. [Devam'a portal.azure.com](https://portal.azure.com/).
2. Diğer uygulamaları **arayın Enterprise açın**.
3. Uygulama türü **filtresini** Microsoft Uygulamaları olarak _değiştirerek_ Uygula'ya **tıklayın**.
4. Modern Çalışma Alanı Müşteri _API'lerini arayın ve seçin_.
5. Sol **tarafta bölmeden** Kullanıcılar ve gruplar'ı seçin ve ardından + Kullanıcı/ **grup ekle'yi seçin**.
6. Kullanıcılar ve gruplar'dan istediğiniz **grubu arama**.
7. Bir rol seçin öğesinin altında **uygun rolü arayın** ve sonra rolü seçin.
8. **Ata'ya seçin**.

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Microsoft Yönetilen Masaüstü ile çalışmaya başlama adımları

1. Access yönetici portalı (bu makale).
1. [Yönetici portalında yönetici kişilerini ekleyin ve doğrulayın](add-admin-contacts.md).
1. [Kayıt sonrasında ayarları ayarlayın](conditional-access.md).
1. Diğer uygulamaları dağıtın [ve Intune Şirket Portalı](company-portal.md).
1. [Lisans atama](assign-licenses.md).
1. [Uygulamaları dağıtın](deploy-apps.md).
1. [Cihazları ayarlayın](set-up-devices.md).
1. [AutoPilot ve Kayıt Durumu Sayfası ile ilk çalıştırma deneyimini ayarlayın](esp-first-run.md).
1. [Kullanıcı desteği özelliklerini etkinleştirin](enable-support.md).
1. [Kullanıcılarınızı cihazları kullanmaya hazır hale hazırlayın](get-started-devices.md).
1. [Uygulama denetimi ile çalışmaya başlama](get-started-app-control.md).
