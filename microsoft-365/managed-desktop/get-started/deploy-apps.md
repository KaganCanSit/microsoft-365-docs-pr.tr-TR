---
title: Uygulamaları cihazlara dağıtma
description: Microsoft Yönetilen Masaüstü cihazlarına uygulama ekleme ve uygulama dağıtma hakkında bilgiler.
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler, uygulamalar, iş hattı uygulamaları, LOB uygulamaları
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 7e4ee96fb336205633430f34111d3d845c1f0e6e
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2022
ms.locfileid: "63016438"
---
# <a name="deploy-apps-to-devices"></a>Uygulamaları cihazlara dağıtma

Microsoft Yönetilen Masaüstü'ne eklemenin bir parçası olarak, kullanıcı cihazlarınıza uygulama ekleme ve dağıtma da dahildir. Microsoft Yönetilen Masaüstü portalını kullandıktan sonra uygulamalarınızı ekleyebilir ve dağıtabilirsiniz.

Genel olarak süreç şöyle olur:

1. Microsoft Yönetilen Masaüstü [portalına](#1) uygulama ekleme: Bu uygulamalar mevcut iş hattı (LOB) uygulamaları veya Intune ile İş İçin Microsoft Store iş sitelerinden gelen uygulamalar olabilir.
2. [Uygulama Azure Active Directory için bir grup (AD) grubu oluşturun](#2): Uygulama atamalarını yönetmek için bu grupları kullanırsanız.
3. [Uygulamaları kullanıcılarınıza attayabilirsiniz](#3).

<span id="1" />

## <a name="step-1-add-apps-to-microsoft-managed-desktop-portal"></a>1. Adım: Microsoft Yönetilen Masaüstü portalına uygulama ekleme

[Win32 veya Windows MSI](#lob-apps) tabanlı uygulamalar ya da microsoft [İş İçin Microsoft Store](#msfb-apps) uygulamaları Microsoft Yönetilen Masaüstü'ne ekleyebilir ve ardından bunları Microsoft Yönetilen Masaüstü cihazlarına dağıtabilirsiniz.

<span id="lob-apps">

### <a name="win32-or-windows-msi-based-apps-to-microsoft-managed-desktop"></a>MSI tabanlı Windows Microsoft Yönetilen Masaüstü'ne Win32 veya Masaüstü

İş hattı (LOB) uygulamalarınızı Microsoft Yönetilen Masaüstü portalına  eklersiniz. Microsoft Yönetilen Masaüstü cihazlarına yüklenmiş uygulamalar için gereksinim bilgileri için bkz [. Microsoft Yönetilen Masaüstü uygulaması gereksinimleri](../service-description/mmd-app-requirements.md).

Bu yordamda, ne tür bir uygulama eklemek istediğiniz seçin ve sonra uygulama kaynağını yapılandırarak karşıya yükleyin.

**LOB uygulamanızı veya Windows Microsoft Yönetilen Masaüstü portalına eklemek için:**

Microsoft Yönetilen Masaüstü portalında oturum açın veya Intune'da oturum açın ve Ardından Microsoft Yönetilen Masaüstü'nü arayın. Aşağıdaki Microsoft Yönetilen Masaüstü portalında oturum açma gösteririz:

1. Microsoft Yönetilen Masaüstü [Yöneticisi portalında oturum açın](https://aka.ms/mmdportal).
2. **Stok'ın** altında **Uygulamalar'ı seçin**.
3. Uygulamalar iş yükü bölümünde Ekle'yi **seçin**.
4. Uygulama **ekle'de** İş **için uygulama satırı veya Uygulama** Windows **(Win32)'yi seçin**.
    - İş hattı **uygulamasını** seçtiysanız, İş hattı uygulamalarını [ekleme ve yapılandırmaya](/intune/lob-apps-windows) Windows için bkz. Microsoft Intune iş hattı uygulaması ekleme.
    - Uygulama ekleme (**Win32) Windows**, bkz. Uygulama ekleme ve yapılandırmayla ilgili yönerge için [Win32](/intune/apps-win32-app-management) Windows.

<span id="msfb-apps">

### <a name="microsoft-store-for-business-apps"></a>İş İçin Microsoft Store uygulamaları

İş İçin Microsoft Store'a kaydolmadınız, uygulama satın ayken kaydolabilirsiniz. Uygulamalarınız olduktan sonra bunları Microsoft Yönetilen Masaüstü ile eşitebilirsiniz.

**Web siteden uygulama satın İş İçin Microsoft Store:**

1. İş İçin Microsoft Store Yönetici [hesabınızla](https://businessstore.microsoft.com) oturum İş İçin Microsoft Store açın.
2. **Grubum için alışverişe devam'ı seçin**.
3. İstediğiniz uygulamayı bulmak için Ara'ya kullanın ve uygulamayı seçin.
4. Ürün ayrıntılarında Uygulamayı **Edin'i seçin**.
Microsoft Store, uygulamayı sizin için **ürünler'e** ekler.

**Intune ile OneDrive arasında eşitlemenin etkin İş İçin Microsoft Store için:**

1. İş İçin Microsoft Store Yönetici [hesabınızla](https://businessstore.microsoft.com) oturum İş İçin Microsoft Store açın.
2. **Yönet'i seçin**.
3. **Seçenekler'Ayarlar** sonra da **Dağıt'ı seçin**.
4. Yönetim **araçları altında** Intune'ın listelenmiş olduğunu ve durumunun Etkin olduğunu **doğrulayın**.  

**Intune ile eşitlemeyi zorlamak için şunları İş İçin Microsoft Store:**

1. [Microsoft Endpoint Manager yönetim merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) oturum açın.
2. Kiracı **yönetimi'ne**, ardından **Bağlayıcılar ve belirteçler'e ve** sonra Kiracı **Yönetimi'İş İçin Microsoft Store**.
3. **Eşitlemeyi** etkinleştirme için **Etkin İş İçin Microsoft Store öğesini seçerek Intune ile toplu satın alınan uygulamalara erişebilirsiniz.**
4. Tercih ettiğiniz dili seçin ve ardından **Buradan satın** aldığınız uygulamaları Intune'a Microsoft Store Eşitle'yi seçin.

<span id="2" />

## <a name="step-2-create-azure-ad-groups"></a>2. Adım: Azure AD grupları oluşturma

Her uygulama için üç Azure AD grubu oluşturun. Bu tabloda, size gereken gruplar (Kullanılabilir, Gerekli ve Kaldır) anahattı vardır.

Uygulama atama türü | Grup kullanımı | Örnek Azure AD adı |
--- | --- | --- |
Kullanılabilir |  Uygulama, uygulamanın veya Şirket Portalı sitesinden kullanılabilir. | MMD – *uygulama adı* – Kullanılabilir |
Gerekli |  Uygulama, seçilen gruplarda cihazlara yüklenir. | MMD – *uygulama adı* – Gerekli |
Kaldır |  Uygulama, seçilen gruplarda yer alan cihazlardan kaldırılır. | MMD – *uygulama adı* – Kaldır |

Kullanıcılarınızı bu gruplara şu kişilerden birini ekleyin:

- Uygulamayı kullanılabilir hale
- Uygulamayı yükleyin veya
- Uygulamayı kendi Microsoft Yönetilen Masaüstü cihazından kaldırın.

<span id="3" />

## <a name="step-3-assign-apps-to-your-users"></a>3. Adım: Kullanıcılarınıza uygulama atama

**Uygulamayı kullanıcılarınıza atamak için:**

1. Microsoft Yönetilen Masaüstü [Yöneticisi portalında oturum açın](https://aka.ms/mmdportal).
2. Yönetilen Masaüstü bölmesinde Uygulamalar'ı **seçin**.
3. Uygulamalar iş yükü bölümünde, kullanıcıları atamak istediğiniz uygulamayı seçin ve Kullanıcı grupları **ata'ya tıklayın**.
4. Belirli bir uygulama için bir ödev türü seçin (Uygun, Gerekli, Kaldır) ve uygun grubu attayabilirsiniz.
5. Uygulama Ata bölmesinde Tamam'ı **seçin**.

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Microsoft Yönetilen Masaüstü ile çalışmaya başlama adımları

1. Access [yönetici portalı](access-admin-portal.md).
1. [Yönetici portalında yönetici kişilerini ekleyin ve doğrulayın](add-admin-contacts.md).
1. [Kayıt sonrasında ayarları ayarlayın](conditional-access.md).
1. Dağıtım ve [Intune Şirket Portalı](company-portal.md).
1. [Lisans atama](assign-licenses.md).
1. Uygulamaları dağıtın (bu makale).
1. [Cihazları ayarlayın](set-up-devices.md).
1. [AutoPilot ve Kayıt Durumu Sayfası ile ilk çalıştırma deneyimini ayarlayın](esp-first-run.md).
1. [Kullanıcı desteği özelliklerini etkinleştirin](enable-support.md).
1. [Kullanıcılarınızı cihazları kullanmaya hazır hale hazırlayın](get-started-devices.md).
1. [Uygulama denetimi ile çalışmaya başlama](get-started-app-control.md).

<!--# Preparing apps for Microsoft Managed Desktop

This topic is the target for 2 "Learn more" links in the Admin Portal (aka.ms/app-overview;app-package); also target for link from Online resources (aka.ms/app-overviewmmd-app-prep) do not delete.

-->
