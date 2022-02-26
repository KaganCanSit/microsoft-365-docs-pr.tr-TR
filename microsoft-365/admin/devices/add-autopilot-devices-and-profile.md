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
description: AutoPilot'Windows kullanabileceğiniz, Windows 10 kullanıma hazır olacak şekilde işletmenize uygun yeni cihaz ayarlamayı öğrenin.
ms.openlocfilehash: 4b187d5e8f9acc8fb76e77770ec88790394dfbe3
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973845"
---
# <a name="use-the-step-by-step-guide-to-add-autopilot-devices-and-profile"></a>AutoPilot cihaz ve profilleri eklemek için adım adım kılavuzu kullanın.

Windows AutoPilot Windows 10 u kullanarak işletmenize uygun yeni cihaz  ve cihazları çalışanlarınıza verirken kullanıma hazır hale kullanabilirsiniz.
  
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
  
3. Cihaz **Upload .csv bir dosyada**, dosyanın hazır bulunduğu konuma gidin ve .CSV **Aç'ı** \> **seçin**. Dosyada üç üst bilgi olması gerekir:
    
    - A sütunu: Cihaz Seri Numarası
    
    - B sütunu: Windows Ürün Kimliği
    
    - C sütunu: Donanım Numarası
    
    Bu bilgileri donanım satıcıdan edinebilirsiniz veya CSV dosyası oluşturmak için [Get-WindowsAutoPilotInfo PowerShell](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) betiği kullanabilirsiniz. 
    
    Daha fazla bilgi için bkz. [Cihaz listesi CSV dosyası](../misc/device-list.md). **Cihaz listesiyle .csv dosyası yükleme** sayfasında bir örnek dosya da indirebilirsiniz. 
    
> [!NOTE]
> Bu betikte, müşterinin cihazı AutoPilot'a kaydetmesi için gereken özellikleri almak Windows kullanılır. Sonuçta elde edilen CSV dosyasının Windows Ürün Kimliği (PKID) değeri toplamamalerinin normal olduğunu unutmayın, çünkü bu bir cihazı kaydetmek için gerekli değildir ve PKID'nin CSV çıktısı içinde NULL olması tamamen sorun değildir. Yalnızca seri numarası ve donanım karması doldurulur.
    
4. Profil **atama sayfasında** mevcut bir profili seçebilirsiniz veya yeni bir profil oluşturabilirsiniz. Henüz bir tane yoksa, oluşturmak için bir hesap oluşturmanız istenir. 
    
    Profil, tek bir cihaza veya bir cihaz grubuna uygulanabilen ayarlar koleksiyonudur.
    
    Varsayılan özellikler gereklidir ve otomatik olarak ayarlanır. Varsayılan özellikler şunlardır:
    
    - Kayıt Cortana, OneDrive OEM kaydı'OneDrive atlayabilirsiniz.
    
    - Şirketinizin markasıyla oturum açma deneyimi oluşturma.
    
    - Bağlan hesaplarınıza Azure Active Directory için cihazlarınızı seçin ve bu hesapları sizin yönetilleri için otomatik olarak Microsoft 365 İş Ekstra.
    
    Daha fazla bilgi için bkz [. AutoPilot Profili ayarları hakkında](autopilot-profile-settings.md). 
    
5. Diğer ayarlar, **Gizlilik ayarlarını atla** ve **Kullanıcının yerel yönetici olmasına izin verme** şeklindedir. Varsayılan olarak ikisi de **Kapalı** durumdadır. 
    
    **İleri**'yi seçin.
    
6. **Hepsi bu kadar,** oluşturduğunuz (veya seçtiğiniz) profilin, cihaz listesini yükerek oluşturduğunuz cihaz grubuna uygulanıyor olduğu gösterir. Ayarlar, cihaz kullanıcıları bir sonraki oturum açmada etkili olur. **Kapat**'ı seçin.

## <a name="related-content"></a>İlgili içerik

[AutoPilot Profili ayarları hakkında](autopilot-profile-settings.md) (makale)\
[Cihazlarınızı ve uygulama verilerinizi koruma seçenekleri](../devices/choose-device-security.md) (makale)
