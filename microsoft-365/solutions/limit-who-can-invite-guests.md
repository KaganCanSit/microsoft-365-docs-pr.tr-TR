---
title: Konukları davet edecek kişileri sınırlama
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-collaboration
- m365solution-securecollab
- m365solution-scenario
- m365initiative-externalcollab
ms.localizationpriority: medium
f1.keywords: NOCSH
recommendations: false
description: Kimlerin, organizasyona konuk davet edecek kişileri sınırlandırma hakkında bilgi öğrenin.
ms.openlocfilehash: d8eb9452abb76916940d10fa042dae479358568a
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2022
ms.locfileid: "63717348"
---
# <a name="limit-who-can-invite-guests"></a>Konukları davet edecek kişileri sınırlama

Organizasyonda kimlerin konuk davet edey davetiyesi a sınırlaması  olabilir. Konuk hesapları, ekipleri paylaşmak, siteleri, SharePoint ve klasörleri kuruluş dışındaki diğer kişilerle paylaşmak için kullanılabilir.

İş süreçleriniz için kimlerin konukla paylaşımda sınırlayabileceklerini sınırlamanız gerekiyorsa veya kullanıcıların eğitimi tamamlamak için konuklarla paylaşabileceklerini sınırlandırabilirsiniz. Bunun için, işletmede konuk davetli rolünü kullanarak kimleri paylaşabileceklerini Azure Active Directory.

## <a name="create-a-security-group-for-people-allowed-to-invite-guests"></a>Konuk davet etmelerine izin verilen kişiler için güvenlik grubu oluşturma

İlk adım, konukları davet etme izni olan kullanıcılar için bir güvenlik grubu oluşturmaktır. Bu grubu Azure AD rolüne izin verecek şekilde yapılandırdığınızdan emin olun ve ardından buna Konuk davetli rolü attayın.

Konuk davetliler için güvenlik grubu oluşturmak için
1. Genel yönetici veya [Azure Active Directory](https://aad.portal.azure.com) Yöneticisi hesabını kullanarak e-posta hesabınızla oturum açın.
1. **Active Directory sayfasında Gruplar'ı** ve **ardından** Yeni **grup'a tıklayın**.
1. Grup **türü** için **Güvenlik'i seçin**.
1. Bir Grup **adı yazın.** 
1. İsteğe bağlı olarak, grup için bir açıklama ekleyin.
1. Azure **AD rolleri gruba atanabilir için Evet'i** **seçin**.
1. Grup sahipleri ve üyeleri ekleyin.
1. **Roller'in** altında Rol **yok seçili'yi seçin**.
1. Konuk davetlisi rolünü **arayın ve** seçin, ardından Seç'i **seçin**.
1. **Oluştur'a** seçin ve bir gruba hangi rollerin atanabilir olduğunu onaylayın. Grubunuz oluşturulur ve üye eklemeniz için hazır olur.

## <a name="configure-external-collaboration-settings"></a>Dış işbirliği ayarlarını yapılandırma

Güvenlik grubunu oluşturduktan ve konukları davet etmek istediğiniz kullanıcıları eklediktan sonra, bir sonraki adım Azure AD dış işbirliği ayarlarını yalnızca Konuk davetlisi rolüne sahip olan kullanıcıların konuk davet etmelerine izin verecek şekilde yapılandırmaktır.

Genel yöneticilerin bu ayardan bağımsız olarak her zaman konukları davet ety defterine bakabilirsiniz.

> [!NOTE]
> Kiracılar arası erişim ayarlarında yapılan değişikliklerin yürürlüğe girecekleri iki saat sürebilir.

Azure AD'yi konuk davetlerini Konuk davetlisi rolüyle sınırlandır olacak şekilde yapılandırmak için
1. Dış [Azure Active Directory'i](https://aad.portal.azure.com/) **seçin**.
1. Dış **işbirliği ayarları'ı seçin**.
1. Konuk **daveti ayarları'nın** altında Yalnızca **belirli yönetici rollerine atanan kullanıcılar konukları davet edebilirsiniz'i seçin**.
1. **Kaydet**'i seçin.

## <a name="related-topics"></a>İlgili konular

[Yalnızca belirli güvenlik gruplarında yer alan kullanıcıların dış paylaşımda ve gruplarda SharePoint izin OneDrive](/sharepoint/manage-security-groups)

[B2B dış işbirliğini etkinleştirme ve konukları kimlerin davet edebileceğini yönetme](/azure/active-directory/external-identities/delegate-invitations)