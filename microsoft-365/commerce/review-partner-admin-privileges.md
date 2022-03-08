---
title: İş ortağı yönetim ayrıcalıklarını gözden geçirme
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: jamitche, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_subscriptions
search.appverid: MET150
description: Hangi yönetici ayrıcalıklarına sahip olduklarını belirlemek için Microsoft onaylı çözüm sağlayıcıları (iş ortakları) listenizi gözden geçirmeyi ve bu ayrıcalıkları kaldırmayı öğrenin.
ms.date: 12/03/2021
ms.openlocfilehash: 067716689bd82e67dda357d675383ef2541b1dc3
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63318431"
---
# <a name="review-partner-administrative-privileges"></a>İş ortağı yönetim ayrıcalıklarını gözden geçirme

Microsoft sertifikalı bir bulut çözümü sağlayıcınız (bayi iş ortağı) varsa, onlara atanmış temsili yönetim ayrıcalıklarının (DAP) üç aylık incelemesini yürütmenizi öneririz. Kuruluşun, bu iş ortağının sizin adına kuruluş verilerinize erişmesi ve satın almalar yapmalarını istediğiden emin olun.

> [!IMPORTANT]
> Genel yönetici izinleri içeren DAP'nin herhangi bir iş ortağına verilmesi güvenlik riski sunabilirsiniz. Çok fazla Genel yönetici olması da bir güvenlik riski sağlar. [Temsilcili ayrıcalıkları hedef alan en son etkinlik hakkında daha fazla bilgi öğrenin](https://www.microsoft.com/security/blog/2021/10/25/nobelium-targeting-delegated-administrative-privileges-to-facilitate-broader-attacks/).

Bir bayi iş ortağından DAP sözleşmesini kabul ettikten sonra, çalışanlarınıza Genel yönetici rolü atamaktadırlar. Genel yönetici rolü, iş ortağının çalışanlarına çalışanlarının kişisel verilerine ve diğer hassas bilgilere erişmelerini sağlar. Ayrıca, aşağıdaki eylemler gibi kiracı genelinde işlem yapmak için onlara izin de verir:

- Kullanıcı parolalarını değiştirme
- E-posta hesaplarıyla kullanıcı ekleme
- Organizasyonuyla ilişkilendirilmiş web etki alanlarını ekleme ve yönetme

DAP etkinleştirildiğinde, iş ortağınız tarafından eklensin Genel yöneticilerin sayısı üzerinde hiçbir denetiminiz olmaz. Hesabınıza yalnızca iş ortağı DAP (Genel yönetici) erişimini kabul edebilir veya reddedebilirsiniz.

## <a name="review-and-remove-roles-from-partners"></a>İş ortaklarının rollerini gözden geçirme ve kaldırma

1. Sayfa Microsoft 365 yönetim merkezi, Ayarlar  > <a href="https://go.microsoft.com/fwlink/p/?linkid=2074649" target="_blank">Partner ilişkileri sayfasına</a> gidin. DAP iş ortaklarının **Roller sütununda** Genel Yönetici **listelenir** .
2. İş ortağından Genel yönetici rolünü kaldırmak için, kaldırmak istediğiniz iş ortağının adını bulun.
3. İlişki Türü olarak **Bayi'in** olduğu **satırı seçin**.
4. İş ortağı ayrıntıları sayfasında Rolleri **kaldır'ı seçin ve** sonra da Evet'i **seçin**.

> [!NOTE]
>
> - bir iş ortağından DAP'yi (Genel yönetici rolü) kaldırırsanız, gelecekteki hizmet teslimi hakkında tartışmak için bu iş ortağıyla görüşmenizi öneririz. Örneğin, daha düşük ayrıcalıklara sahip bir kullanıcı hesabı oluşturabilir ve bu hesap bilgilerini iş ortağınız ile paylaşabilirsiniz. Kullanıcıları ekleme ve [yönetici rolleri atama](../admin/add-users/add-users.md) hakkında [daha fazla bilgi edinebilirsiniz](../admin/add-users/assign-admin-roles.md).
> - Genel yönetici rolü kaldırılmış olsa bile iş ortağı sizin adına satın almalar yapmaya devam ediyor olabilir. İş Ortağı Merkezi'nde bu özelliği kaldırmalarını istemek için iş ortağıyla bağlantı kurmanız önerilir.

## <a name="related-content"></a>İlgili içerik

[İş ortağı ilişkilerini yönetme](manage-partners.md) (makale)\
[Yönetici rolleri hakkında](../admin/add-users/about-admin-roles.md) (makale)\
[Azure AD'de yönetici ayrıcalıkları temsili](/partner-center/customers-revoke-admin-privileges#delegated-admin-privileges-in-azure-ad) (makale)
