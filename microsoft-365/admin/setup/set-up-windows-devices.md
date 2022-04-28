---
title: Microsoft 365 İş Ekstra kullanıcılar için Windows cihazları ayarlama
f1.keywords:
- CSH
ms.author: deniseb
author: denisebmsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- TRN_M365B
- OKR_SMB_Videos
- seo-marvel-mar
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- adminvideo
search.appverid:
- BCS160
- MET150
ms.assetid: 2d7ff45e-0da0-4caa-89a9-48cabf41f193
description: Microsoft 365 İş Ekstra kullanıcılar için Windows 10 Pro çalıştıran Windows cihazları ayarlayarak merkezi yönetim ve güvenlik denetimlerini etkinleştirme.
ms.openlocfilehash: 57db37f73d2b9145f7c4fb9c1ee1005318c629d7
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096236"
---
# <a name="set-up-windows-devices-for-microsoft-365-business-premium-users"></a>Microsoft 365 İş Ekstra kullanıcılar için Windows cihazları ayarlama

## <a name="before-you-begin"></a>Başlamadan önce

Microsoft 365 İş Ekstra kullanıcılar için Windows cihazları ayarlamadan önce tüm Windows cihazların Windows 10 Pro, sürüm 1703 (Creators Update) veya Windows 11 Pro çalıştığından emin olun. 

Windows 10 Pro (veya Windows 11 Pro), Windows 10 Pro ve Windows 11 Pro tamamlayan bir dizi bulut hizmeti ve cihaz yönetimi özelliği olan Windows 10 Business dağıtmak için önkoşuldur ve Microsoft 365 İş Ekstra merkezi yönetim ve güvenlik denetimlerini etkinleştirin.

[Microsoft 365 İş Ekstra gereksinimleri hakkında daha fazla bilgi edinin](https://www.microsoft.com/microsoft-365/business/microsoft-365-business-premium?activetab=pivot:techspecstab).

## <a name="windows-10-pro-and-windows-11-pro"></a>Windows 10 Pro ve Windows 11 Pro

Windows 7 Pro, Windows 8 Pro veya Windows 8.1 Pro gibi Windows önceki sürümlerini çalıştıran Windows cihazlarınız varsa, Microsoft 365 İş Ekstra aboneliğiniz bunları yükseltmenizi sağlar Windows 10 Pro veya Windows 11 Pro cihazlar.
  
Windows cihazları yükseltme hakkında daha fazla bilgi için aşağıdaki makalelere bakın:

- [giriş Windows Windows Pro yükseltme](https://support.microsoft.com/windows/upgrade-windows-home-to-windows-pro-ef34d520-e73f-3198-c525-d1a218cc2818)
- [Windows 10 Pro'ye yükseltme](https://support.microsoft.com/windows/upgrade-to-windows-10-pro-71ecc746-0f81-a4c0-bd4b-0db8559e0796)
  
Yükselttikten sonra, [yükseltmeye sahip olduğunuzu doğrulamak veya yükseltmenin çalıştığından emin olmak için bkz. Cihazın Azure AD'ye bağlı olduğunu](#verify-the-device-is-connected-to-azure-ad) doğrulama.

## <a name="join-windows-devices-to-your-organizations-azure-ad"></a>Windows cihazları kuruluşunuzun Azure AD'sine ekleme

Şirketinizin tüm Windows cihazları Windows 10 Pro veya Windows 11 Pro çalıştırıyorsa, bu cihazları kuruluşunuzun Azure Active Directory (Azure AD) ile birleştirebilirsiniz. 

1. Windows bir cihazda Windows logosunu ve ardından Ayarlar simgesini seçin.
  
2. **Ayarlar'de** **AccountsAccess** >  **iş veya okul** \> **Bağlan** gidin.
  
3. E-posta adresinizi yazın ve **İleri'yi** seçin.

4. İşlemi tamamlamak için istemleri izleyin.

## <a name="verify-the-device-is-connected-to-azure-ad"></a>Cihazın Azure AD'ye bağlı olduğunu doğrulama

Eşitleme durumunuzu doğrulamak için, **Ayarlar'daki İşe veya okula erişim** sayfasında, **Bilgi** ve **Bağlantıyı Kes** düğmelerini kullanıma açmak **için _** _ \<organization name\> konumuna bağlı alanını seçin. Eşitleme durumunuzu almak için **Bilgi'yi** seçin. 
  
**Eşitleme durumu** sayfasında **Eşitle'yi** seçerek bilgisayara en son mobil cihaz yönetimi ilkelerini alın.  
  
## <a name="next-steps"></a>Sonraki adımlar

Mobil cihazlarınızı ayarlamak için bkz[. Microsoft 365 İş Ekstra kullanıcılar için mobil cihazları ayarlama](set-up-mobile-devices.md), 

Korumayı artırmak için bkz. [İş planları için Microsoft 365 güvenliğini sağlamanın en iyi 10 yolu](../security-and-compliance/secure-your-business-data.md).
  

