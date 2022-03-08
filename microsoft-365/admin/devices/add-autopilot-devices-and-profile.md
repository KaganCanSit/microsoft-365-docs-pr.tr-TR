---
title: AutoPilot cihaz ve profilleri eklemek için adım adım kılavuzu kullanın.
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.localizationpriority: medium
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: be5b6d90-3344-4c5e-bf40-5733eb845beb
description: AutoPilot'Windows iş için çalışan kullanımına hazır olacak Windows 10 cihazları ayarlamak üzere nasıl kullanabileceğinizi öğrenin.
ms.openlocfilehash: 12e86102633ddfc19960fb561b2a626da29f0560
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314021"
---
# <a name="use-the-step-by-step-guide-to-add-autopilot-devices-and-profile"></a>AutoPilot cihaz ve profilleri eklemek için adım adım kılavuzu kullanın.

> [!NOTE]
> İş için Microsoft Defender 1 Mart 2022 Microsoft 365 İş Ekstra müşterilere sunulmaktadır. Bu teklif, cihazlar için ek güvenlik özellikleri sağlar. [İş için Defender hakkında daha fazla bilgi öğrenin](../../security/defender-business/mdb-overview.md).

Windows AutoPilot Windows 10 u kullanarak işletmenize uygun yeni cihaz ve  cihazları çalışanlarınıza vermek üzere kullanıma hazır hale kullanabilirsiniz.
  
## <a name="device-requirements"></a>Cihaz gereksinimleri

Cihazlar şu gereksinimleri karşılamalıdır:
  
- Windows 10, sürüm 1703 veya sonrası
    
- Henüz ilk ve en son Windows yeni cihazlar
    
## <a name="use-the-setup-guide-to-create-devices-and-profiles"></a>Cihaz ve profil oluşturmak için kurulum kılavuzunu kullanma

Henüz cihaz grupları veya profil oluşturmadınız, başlamanın en iyi yolu adım adım kılavuzu kullanmaktır. Ayrıca, kılavuzu [kullanmadan](create-and-edit-autopilot-devices.md) [cihazlar ekleyebilir ve](create-and-edit-autopilot-profiles.md) onlara profil atabilirsiniz. 
  
1. yönetim merkezine gidin <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>.

2. Sol gezinti bölmesinde Cihazlar **AutoPilot'ı** \> seçin.

    ![Yönetim merkezinde cihazlar'ı ve ardından AutoPilot'ı seçin.](../../media/AutoPilot.png)
  
2. **AutoPilot sayfasında Kılavuzu** başlat'a tıklayın **veya dokunun**.
    
    ![Click Start guide for step-by-step instructions for Autopilot.](../../media/31662655-d1e6-437d-87ea-c0dec5da56f7.png)
  
3. Cihaz **Upload .csv bir dosyada**, kendi dosyanız için hazır bulunduğu konuma gidin ve .CSV **Aç'ı** \> **seçin**. Dosyada üç üst bilgi olması gerekir:
    
    - A sütunu: Cihaz Seri Numarası
    
    - B sütunu: Windows Ürün Kimliği
    
    - C sütunu: Donanım Numarası
    
    Bu bilgileri donanım satıcıdan edinebilirsiniz veya CSV dosyası oluşturmak için [Get-WindowsAutoPilotInfo PowerShell](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) betiği kullanabilirsiniz. 
    
    Daha fazla bilgi için bkz. [Cihaz listesi CSV dosyası](../misc/device-list.md). **Cihaz listesiyle .csv dosyası yükleme** sayfasında bir örnek dosya da indirebilirsiniz. 
    
> [!NOTE]
> Bu betikte, müşterinin cihazı AutoPilot'a kaydetmesi için gereken özellikleri almak Windows kullanılır. Sonuçta elde edilen CSV dosyasının Windows Ürün Kimliği (PKID) değeri toplamamalerinin normal olduğunu unutmayın; çünkü bu bir cihazı kaydetmek için gerekli değildir ve PKID'nin CSV çıktısı içinde NULL olması tamamen sorun değildir. Yalnızca seri numarası ve donanım karması doldurulur.
    
4. Profil **atama sayfasında** mevcut bir profili seçebilirsiniz veya yeni bir profil oluşturabilirsiniz. Henüz bir tane yoksa, oluşturmak için bir hesap oluşturmanız istenir. 
    
    Profil, tek bir cihaza veya bir cihaz grubuna uygulanabilen ayarlar koleksiyonudur.
    
    Varsayılan özellikler gereklidir ve otomatik olarak ayarlanır. Varsayılan özellikler şunlardır:
    
    - Kayıt Cortana, OneDrive OEM kaydı atlayabilirsiniz.
    
    - Şirketinizin markasıyla oturum açma deneyimi oluşturma.
    
    - Bağlan hesaplarınıza Azure Active Directory ve tüm cihazlarınız tarafından yönetilleri için otomatik olarak Microsoft 365 İş Ekstra.
    
    Daha fazla bilgi için bkz [. AutoPilot Profili ayarları hakkında](autopilot-profile-settings.md). 
    
5. Diğer ayarlar, **Gizlilik ayarlarını atla** ve **Kullanıcının yerel yönetici olmasına izin verme** şeklindedir. Varsayılan olarak ikisi de **Kapalı** durumdadır. 
    
    **İleri**'yi seçin.
    
6. **Hepsi bu kadar,** oluşturduğunuz (veya seçtiğiniz) profilin, cihaz listesini yükerek oluşturduğunuz cihaz grubuna uygulanıyor olduğu gösterir. Ayarlar, cihaz kullanıcıları bir sonraki oturum açmada etkili olur. **Kapat**'ı seçin.

## <a name="related-content"></a>İlgili içerik

[AutoPilot Profili ayarları hakkında](autopilot-profile-settings.md) (makale)\
[Cihazlarınızı ve uygulama verilerinizi koruma seçenekleri](../devices/choose-device-security.md) (makale) İşletmeler için planlarda güvenliği sağlamanın en [Microsoft 365 10 yolu](../security-and-compliance/secure-your-business-data.md)