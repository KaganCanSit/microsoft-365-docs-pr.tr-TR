---
title: Konuk hesapları için önkoşullar
description: Konuk hesapları için yapılandırma yönergeleri ve bunları ayarlama
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 80770c6c122cc4e2892c22a43f185ffbac40c637
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/10/2022
ms.locfileid: "63027557"
---
# <a name="prerequisites-for-guest-accounts"></a>Konuk hesapları için önkoşullar

## <a name="external-collaboration-settings"></a>Dış işbirliği ayarları

Microsoft Yönetilen Masaüstü, konuk hesabı erişimi için Azure AD kuruluşta aşağıdaki yapılandırmayı öneririz. Bu ayarları Azure portalında [Dış Kimlikler](https://portal.azure.com) **/ Dış işbirliği ayarları altında ayarlayabilirsiniz**:

| Ayar | Şu şekilde ayarla: |
| ------ | ------ |
| Konuk erişimi | Konukların dizin nesnelerinin özelliklerine ve üyeliklerine erişimi sınırlıdır. |
| Konuk daveti ayarları | Belirli yönetici rollerine atanan üye kullanıcılar ve kullanıcılar, üye izinlerine sahip konuklar da dahil olmak üzere konukları davetlayabilir |

Microsoft Yönetilen Masaüstü'ne konuk hesabı erişimi için Azure AD kuruluşu içinde aşağıdaki yapılandırma gerekir. Bu ayarı Azure portalında [Dış Kimlikler](https://portal.azure.com) **/ Dış işbirliği ayarları altında ayarlayabilirsiniz**:

| Ayar | Seçenek |
| ------ | ------ |
| İşbirliği kısıtlamaları | Bu seçeneklerden herhangi birini seçin: <ul><li>Herhangi bir etki **alanına davet gönderilmeye izin ver (en çok dahil)** seçeneğini belirtirse başka yapılandırma gerekmez.</li><li>Belirtilen etki **alanlarına davetleri reddet'i** seçerek hedef Microsoft.com etki alanlarında davetlerin listelenmiyor olduğundan emin olun.</li><li>Yalnızca belirtilen etki **alanlarına (en kısıtlayıcı) davetlere izin ver'i** seçerek, davetlerin Microsoft.com *etki* alanlarında listelenmiş olduğundan emin olun.</li><ul>

Bu ayarlarla etkileşimde bulunan kısıtlamalar ayarlarsanız Modern Çalışma Alanı Hizmeti Hesaplarının kullanıcılarını Azure Active Directory **emin olun**. Örneğin, konuk hesaplarının Intune portalına erişimini engelleyen bir koşullu erişim ilkenize sahipseniz **Modern** Çalışma Alanı Hizmeti Hesapları grubunu bu ilkenin dışında tutabilirsiniz.

Daha fazla bilgi için [B2B dış işbirliğini etkinleştirme ve kimlerin konuk davet edebeceklerini yönetme.](/azure/active-directory/external-identities/delegate-invitations#to-configure-external-collaboration-settings)

## <a name="unlicensed-intune-admin"></a>Lisanssız Intune yöneticisi

**Lisanssız yöneticilere erişime izin ver** ayarı etkinleştirilmelidir. Bu ayar etkinleştirilmemişse, hizmet için Azure AD organizasyona erişmeye deneildiğinde hata oluşabilir. Güvenlik üzerindeki etkilerini kaygılanmadan bu ayarı güvenle etkinleştirebilirsiniz. Erişim kapsamı, işlem personelimiz de dahil olmak üzere kullanıcılara atanan roller tarafından tanımlanır.

**Bu ayarı etkinleştirmek için:**

1. Microsoft Endpoint Manager [yönetim merkezine gidin](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Kiracı **yönetimi'ne gidin**, Roller'i **seçin**. Ardından, Yönetici **lisanslama'ya seçin**.
3. Lisanssız **yöneticilere erişime izin ver bölümünde** Evet'i **seçin**.

> [!IMPORTANT]
> Evet'i seçdikten sonra bu ayarı geri **alamazsanız**.

Daha fazla bilgi için bkz[. Microsoft Intune](/mem/intune/fundamentals/unlicensed-admins).

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Microsoft Yönetilen Masaüstü için hazır adımlar

1. [Microsoft Yönetilen Masaüstü için önkoşulları gözden geçirebilirsiniz](prerequisites.md).
1. Hazırlık [değerlendirme araçlarını çalıştırın](readiness-assessment-tool.md).
1. Satın [Şirket Portalı](../get-started/company-portal.md).
1. Konuk hesapları için önkoşulları gözden geçirme (bu makale).
1. Ağ [yapılandırmasını denetleme](network.md).
1. [Sertifikaları ve ağ profillerini hazırlayın](certs-wifi-lan.md).
1. [Verileri kullanıcı erişimini hazırlama](authentication.md).
1. [Uygulamaları hazırlama](apps.md).
1. [Eşlenmiş sürücüleri hazırlama](mapped-drives.md).
1. [Yazdırma kaynaklarını hazırlama](printing.md).
1. Cihaz [adlarını adresle](address-device-names.md).
