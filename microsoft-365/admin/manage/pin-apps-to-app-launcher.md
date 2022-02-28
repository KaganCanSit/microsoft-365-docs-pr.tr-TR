---
title: Uygulamaları kullanıcılarının uygulama başlatıcısına sabitleme
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.collection:
- Adm_O365
- M365-subscription-management
- Adm_TOC
ms.service: o365-administration
ms.custom: admindeeplinkMAC
ms.localizationpriority: medium
description: Genel yönetici olarak, kullanıcılarının uygulama başlatıcısına üç adede kadar uygulama sabitebilirsiniz.
ms.openlocfilehash: 7ff85e379198312666f03c2d7d6c8bb42b9e08d0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985547"
---
# <a name="pin-apps-to-your-users-app-launcher"></a>Uygulamaları kullanıcılarının uygulama başlatıcısına sabitleme

Azure Active Directory portalında, Office.com adresine ve tüm kullanıcılar için uygulama başlatıcıya üç uygulamaya kadar sabitlemek üzere denetimleri kullanabilirsiniz. Uygulama gruplarını da düzenleyebilirsiniz. Daha sonra eklemiş olacağınız tüm uygulama, kullanıcı tarafından istediğiniz zaman ayrılmış olabilir. Kullanıcılarınız için bir uygulamayı sabitlemek için Bulut uygulaması yöneticisi, Azure Active Directory uygulamasında Uygulama yöneticisi veya Office 365'te Genel yönetici Office 365. Yönetici rolleri hakkında daha fazla bilgi için bkz. [Azure AD'de](/azure/active-directory/roles/permissions-reference) yerleşik roller ve [Microsoft 365](../add-users/about-admin-roles.md). 

Uygulama başlatıcısı ve Office.com hakkında daha fazla bilgi için, uygulama [](https://support.microsoft.com/office/79f12104-6fed-442f-96a0-eb089a3f476a) başlatıcısı ile office.com [güncelleştirmeleri Office 365 makalesine](https://techcommunity.microsoft.com/t5/office-365-blog/updates-to-office-com-and-the-office-365-app-launcher/ba-p/1150503) bakın.

## <a name="use-the-azure-active-directory-portal-to-pin-apps"></a>Uygulamaları sabitlemek Azure Active Directory portalını kullanma

1. Microsoft 365 yönetim merkezi gidin<a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.
2. Sol gezintide, Her şeyi **göster'i seçin** ve Yönetim **merkezleri'nin altında** **Geri Azure Active Directory.**
3. Uygulama **Azure Active Directory**, Enterprise **ayarları'nı** >  **seçin**.
4. Uygulama ekle **Office 365 Ayarlar** Uygulama **ekle'yi seçin**.
5. Kullanıcıların uygulama başlatıcısına sabitlemek istediğiniz uygulamaları seçin ve ardından Ekle'yi **seçin**.

:::image type="content" source="../../media/add-apps.png" alt-text="Microsoft 365 sabitlemek için bu ayarları kullanın.":::

### <a name="pin-a-custom-app"></a>Özel uygulamayı sabitleme

> [!NOTE]
> Kullanıcı arabirimi, bu özelliği kullanmak için ek Azure AD lisansları satın almanız gerektir ihtiyacınız olup olduğunu gösterir. Daha fazla bilgi için Azure Active Directory [bakın](https://azure.microsoft.com/pricing/details/active-directory/).

1. Uygulama **Azure Active Directory**, Tüm **Enterprise sayfasının** >  **üst kısmında Yeni** **uygulama'ya** tıklayın.
2. Uygulama ekle **sayfasında Galeri** dışı  **uygulama'ya veya** uygulamanın önizleme sürümündeyken Kendi uygulamanızı oluşturun'a Azure Active Directory. 
3. Uygulama için bir ad yazın ve ardından Kullanıcılar ve gruplar **sekmesine kullanıcı** attayabilirsiniz.
4. Uygulamanın **simgesini** karşıya yüklemek için Özellikler sekmesini kullanın.
5. Uygulamaya URL atamak için, Çoklu oturum açma sekmesinde **Bağlı'ya tıklayın** ve URL'yi  girin.
6. **Kaydet**'i seçin.

## <a name="create-application-collections"></a>Uygulama koleksiyonları oluşturma

Ayrıca, kuruluşta kullanıcılar için uygulama koleksiyonları da oluşturabilirsiniz. Yönergeler için bkz [. Azure portalında Uygulamalarım portalında koleksiyon oluşturma](/azure/active-directory/manage-apps/access-panel-collections).