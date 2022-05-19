---
title: Güvenlik ekibiniz için e-posta bildirimlerini ayarlama
description: İş için Defender'da güvenlik ekibinize uyarıları ve güvenlik açıklarını bildirmek için e-posta bildirimleri ayarlayın.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection: M365-security-compliance
ms.openlocfilehash: 7dc6c65221211367e080fac46506f209d17f88ff
ms.sourcegitcommit: 60970cf8a2cb451011c423d797dfb77925394f89
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2022
ms.locfileid: "65587456"
---
# <a name="set-up-email-notifications"></a>E-posta bildirimlerini ayarlama

Güvenlik ekibiniz için e-posta bildirimleri ayarlayabilirsiniz. Ardından uyarılar oluşturuldukçe veya yeni güvenlik açıkları keşfedildikçe güvenlik ekibinizdeki kişilere otomatik olarak bildirim gönderilir. 

## <a name="what-to-do"></a>Yapılması gerekenler

1. [E-posta bildirimi türleri hakkında bilgi edinin](#types-of-email-notifications).
2. [E-posta bildirim ayarlarını görüntüleyin ve düzenleyin](#view-and-edit-email-notifications).
3. [Sonraki adımlarınıza geçin](#next-steps).


>
> **Bir dakikan var mı?**
> Lütfen <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">güvenlikle ilgili kısa anketimize</a> katılın. Sizden haber almak isteriz!
>

## <a name="types-of-email-notifications"></a>E-posta bildirimi türleri

E-posta bildirimlerini ayarlarken, aşağıdaki tabloda açıklandığı gibi iki tür arasından seçim yapabilirsiniz:

| Bildirim türü  | Açıklama  |
|---------|---------|
| Güvenlik açıkları  | Her yeni açık veya güvenlik açığı olayı algılandığında, alıcılar bir e-posta alır. |
| Uyarılar & güvenlik açıkları  | Cihazlarda tehditler algılandığından uyarılar oluşturulduğunda veya yeni açıklardan yararlanma veya güvenlik açığı olayları algılandığında alıcılar bir e-posta alır. |

> [!TIP]
> **Güvenlik ekibinizin yeni uyarılar veya güvenlik açıkları hakkında bilgi edinmesi için tek yol e-posta bildirimleri değildir**.
> 
> E-posta bildirimleri, güvenlik ekibinizin gerçek zamanlı olarak bilgilendirilmesine yardımcı olmak için kullanışlı bir yoldur. Ama başkaları da var! Örneğin, güvenlik ekibiniz Microsoft 365 Defender portalında ([https://security.microsoft.com](https://security.microsoft.com) ) her oturum açtığında yeni tehditleri, uyarıları ve güvenlik açıklarını vurgulayan kartlar görür. İş için Defender, güvenlik ekibinizin oturum açar açmaz önem verdiği önemli bilgileri vurgulamak üzere tasarlanmıştır.
> 
> Güvenlik ekibiniz bilgileri görüntülemek için gezinti bölmesinde **Olaylar'ı** da seçebilir. Daha fazla bilgi için bkz. [İş için Microsoft Defender olayları görüntüleme ve yönetme](mdb-view-manage-incidents.md).

## <a name="view-and-edit-email-notifications"></a>E-posta bildirimlerini görüntüleme ve düzenleme

Şirketinizin e-posta bildirim ayarlarını görüntülemek veya düzenlemek için şu adımları izleyin:

1. Microsoft 365 Defender portalına ([https://security.microsoft.com](https://security.microsoft.com)) gidin ve oturum açın.

2. Gezinti bölmesinde **Ayarlar** ve ardından **Uç Noktalar'ı** seçin. Ardından **Genel'in** altında **E-posta bildirimleri'ni** seçin. 

3. Uyarılar ve **Güvenlik Açıkları** sekmelerindeki bilgileri gözden geçirin.

   - **Uyarılar** sekmesinde listelenen herhangi bir öğe görmüyorsanız, uyarılar oluşturulduğunda kişilere bildirilmesi için bir kural oluşturabilirsiniz. Bu görevle ilgili yardım almak için bkz. [Uyarı bildirimleri için kurallar oluşturma](../defender-endpoint/configure-email-notifications.md).

   - **Güvenlik Açıkları** sekmesinde herhangi bir öğe görmüyorsanız, yeni bir güvenlik açığı bulunduğunda kişilere bildirilmesi için bir kural oluşturabilirsiniz. Bu görevle ilgili yardım almak için bkz. [Güvenlik açığı olayları için kurallar oluşturma](../defender-endpoint/configure-vulnerability-email-notifications.md).

   - Oluşturulmuş kurallarınız varsa, düzenlemek için bir kural seçin. Kuralı da silebilirsiniz. 

> [!IMPORTANT]
> İş için Defender'da e-posta bildirimleri ayarladığınızda, bildirim kurallarını belirli kullanıcılara atamanız gerekir. İş için Defender, [Uç Nokta için Defender gibi rol tabanlı erişim denetimi kullanmaz](../defender-endpoint/rbac.md). Ayrıca, e-posta bildirimleri İş için Defender'daki cihaz gruplarına uygulanamaz. 

## <a name="next-steps"></a>Sonraki adımlar

Devam et:

- [4. Adım: Cihazları İş için Microsoft Defender ekleme](mdb-onboard-devices.md)
